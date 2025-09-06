import { useEffect, useState } from 'react';
import { TypingAnimation } from '@/components/TypingAnimation';
import { GitHubStats } from '@/components/GitHubStats';
import { SkillBadges } from '@/components/SkillBadges';
import { ProjectShowcase } from '@/components/ProjectShowcase';
import { AboutSection } from '@/components/AboutSection';

const Index = () => {
  const [showContent, setShowContent] = useState(false);

  useEffect(() => {
    const timer = setTimeout(() => setShowContent(true), 500);
    return () => clearTimeout(timer);
  }, []);

  const roles = [
    "BTech CSE Student",
    "Full-Stack Learner", 
    "Open Source Contributor",
    "Problem Solver",
    "Code Enthusiast"
  ];

  return (
    <div className="min-h-screen bg-background">
      {/* Animated Background */}
      <div className="fixed inset-0 -z-10 overflow-hidden">
        <div className="absolute -top-1/2 -right-1/2 w-full h-full bg-gradient-primary opacity-5 rounded-full animate-pulse-glow" />
        <div className="absolute -bottom-1/2 -left-1/2 w-full h-full bg-gradient-secondary opacity-5 rounded-full animate-pulse-glow" style={{ animationDelay: '1s' }} />
      </div>

      <div className="container mx-auto px-6 py-12 space-y-20">
        {/* Hero Section */}
        <section className={`text-center space-y-8 transition-all duration-1000 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          {/* Profile Image */}
          <div className="relative mx-auto w-32 h-32 mb-8">
            <div className="w-full h-full rounded-full bg-gradient-primary animate-pulse-glow" />
            <div className="absolute inset-2 rounded-full bg-card flex items-center justify-center text-4xl animate-float">
              👨‍💻
            </div>
          </div>

          {/* Name & Title */}
          <div className="space-y-4">
            <h1 className="text-5xl md:text-7xl font-bold bg-gradient-primary bg-clip-text text-transparent animate-fade-up">
              Your Name
            </h1>
            <div className="text-xl md:text-2xl text-muted-foreground h-8">
              <TypingAnimation 
                texts={roles}
                speed={100}
                deleteSpeed={50}
                pauseTime={2000}
                className="font-medium"
              />
            </div>
          </div>

          {/* Welcome Message */}
          <div className={`max-w-3xl mx-auto space-y-4 transition-all duration-1000 delay-300 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}`}>
            <p className="text-lg text-foreground leading-relaxed">
              Welcome to my GitHub profile! 👋 I'm passionate about creating amazing digital experiences
              and solving complex problems through code.
            </p>
            <div className="flex flex-wrap justify-center gap-4 mt-8">
              {[
                { emoji: "📍", text: "India" },
                { emoji: "🎯", text: "Available for opportunities" },
                { emoji: "💻", text: "Love to code" },
                { emoji: "🌱", text: "Always learning" }
              ].map((item, index) => (
                <span 
                  key={item.text}
                  className={`flex items-center space-x-2 px-4 py-2 bg-card border border-card-border rounded-full
                    hover:shadow-glow-primary transition-all duration-300 cursor-pointer hover:scale-105
                    opacity-0 animate-bounce-in-delay-${index + 1}`}
                >
                  <span>{item.emoji}</span>
                  <span className="text-sm font-medium text-foreground">{item.text}</span>
                </span>
              ))}
            </div>
          </div>

          {/* Social Links */}
          <div className={`flex justify-center space-x-6 transition-all duration-1000 delay-500 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'}`}>
            {[
              { name: "GitHub", icon: "🐙", url: "#" },
              { name: "LinkedIn", icon: "💼", url: "#" },
              { name: "Twitter", icon: "🐦", url: "#" },
              { name: "Email", icon: "📧", url: "#" }
            ].map((social, index) => (
              <a
                key={social.name}
                href={social.url}
                className={`group relative w-12 h-12 bg-card border border-card-border rounded-full flex items-center justify-center
                  hover:shadow-glow-accent transition-all duration-300 hover:scale-110 hover:-translate-y-1
                  opacity-0 animate-bounce-in-delay-${index + 1}`}
                title={social.name}
              >
                <span className="text-xl group-hover:scale-110 transition-transform duration-300">
                  {social.icon}
                </span>
                <div className="absolute -bottom-8 left-1/2 transform -translate-x-1/2 px-2 py-1 bg-card border border-card-border rounded text-xs opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                  {social.name}
                </div>
              </a>
            ))}
          </div>
        </section>

        {/* GitHub Stats Section */}
        <section className={`transition-all duration-1000 delay-700 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          <GitHubStats />
        </section>

        {/* About Me Section */}
        <section className={`transition-all duration-1000 delay-900 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          <AboutSection />
        </section>

        {/* Skills Section */}
        <section className={`transition-all duration-1000 delay-1100 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          <SkillBadges />
        </section>

        {/* Projects Section */}
        <section className={`transition-all duration-1000 delay-1300 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          <ProjectShowcase />
        </section>

        {/* Activity Section */}
        <section className={`transition-all duration-1000 delay-1500 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          <div className="text-center space-y-8">
            <h2 className="text-3xl font-bold bg-gradient-accent bg-clip-text text-transparent">
              GitHub Activity
            </h2>
            
            {/* Contribution Graph Placeholder */}
            <div className="bg-card border border-card-border rounded-xl p-8 hover:shadow-glow-success transition-all duration-300">
              <div className="space-y-4">
                <h3 className="text-lg font-semibold text-foreground">📈 Contribution Graph</h3>
                <div className="grid grid-cols-52 gap-1 max-w-4xl mx-auto">
                  {Array.from({ length: 365 }, (_, i) => (
                    <div
                      key={i}
                      className={`w-3 h-3 rounded-sm ${
                        Math.random() > 0.7 ? 'bg-success' :
                        Math.random() > 0.5 ? 'bg-accent opacity-60' :
                        Math.random() > 0.3 ? 'bg-primary opacity-40' :
                        'bg-muted'
                      } hover:scale-125 transition-transform duration-200 cursor-pointer`}
                      title={`${Math.floor(Math.random() * 10)} contributions`}
                    />
                  ))}
                </div>
                <p className="text-sm text-muted-foreground">
                  🔥 Consistent activity throughout the year with <span className="text-success font-semibold">1,847 contributions</span> in the last year
                </p>
              </div>
            </div>

            {/* GitHub Trophies */}
            <div className="bg-card border border-card-border rounded-xl p-8 hover:shadow-glow-warning transition-all duration-300">
              <h3 className="text-lg font-semibold text-foreground mb-6">🏆 GitHub Trophies</h3>
              <div className="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-4">
                {[
                  { trophy: "🥇", name: "MultiLanguage", desc: "Used 5+ languages" },
                  { trophy: "⭐", name: "Stars", desc: "Received 100+ stars" },
                  { trophy: "🍴", name: "Forks", desc: "Received 50+ forks" },
                  { trophy: "📝", name: "Commits", desc: "Made 500+ commits" },
                  { trophy: "🔄", name: "PullRequest", desc: "Created 50+ PRs" },
                  { trophy: "📈", name: "Followers", desc: "Has 100+ followers" }
                ].map((trophy, index) => (
                  <div 
                    key={trophy.name}
                    className={`text-center p-3 bg-muted rounded-lg hover:bg-gradient-warning hover:text-white 
                    transition-all duration-300 cursor-pointer group hover:scale-105
                    opacity-0 animate-bounce-in-delay-${(index % 4) + 1}`}
                  >
                    <div className="text-2xl mb-2 group-hover:animate-bounce">{trophy.trophy}</div>
                    <div className="text-xs font-semibold">{trophy.name}</div>
                    <div className="text-xs opacity-75">{trophy.desc}</div>
                  </div>
                ))}
              </div>
            </div>
          </div>
        </section>

        {/* Footer */}
        <footer className={`text-center py-12 transition-all duration-1000 delay-1700 ${showContent ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'}`}>
          <div className="space-y-4">
            <p className="text-muted-foreground">
              ⚡ Powered by passion and coffee ☕
            </p>
            <p className="text-sm text-muted-foreground">
              Made with ❤️ using React, TypeScript & Tailwind CSS
            </p>
            <div className="flex justify-center items-center space-x-2 text-xs text-muted-foreground">
              <span>Last updated:</span>
              <span className="font-mono bg-muted px-2 py-1 rounded">
                {new Date().toLocaleDateString()}
              </span>
            </div>
          </div>
        </footer>
      </div>
    </div>
  );
};

export default Index;
