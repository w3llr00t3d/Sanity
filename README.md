# Sanity
Maintain sanity on the bird app

Automation:
Visit https://twitter.com/settings/muted_keywords
Open your browser's dev tools (note: this does work in Chrome)
Paste the following code in: (note you may have to clear your existing mute list first)

    const delayMs = 500; // change this if you feel like its running too fast

    const keywords = `leaving twitter
    elon
    el0n
    musk
    elno
    mastodon
    political
    politics
    trump
    donald
    fake news
    make america great again
    covfefe
    alt right
    far right
    right wing
    left wing
    potus
    fascism
    nazis
    liberals
    fascist
    libtard
    maga
    realdonaldtrump
    gop
    biden
    putin
    donaldtrump
    supreme court
    democrat
    republicans
    cuckservatives
    trudeau
    gun control
    democratic party
    merkel
    hilllary clinton
    republican
    trumpism
    leftist
    rnc
    dnc
    obamacare
    senator
    kim yong un
    hillary
    boris johnson
    eric trump
    macron
    obama
    clinton
    erdogan
    piers morgan
    nigel farage
    sean hannity
    kim jong un
    north korea
    pyongyang
    iraq
    iran
    china
    taiwan
    isis
    taliban
    terrorism
    terrorist
    ukraine
    russia
    ukranian
    russian
    nuclear
    wwiii
    ww3
    kardashians
    kardashian
    kylie jenner
    jake paul
    kendall jenner
    kris jenner
    msnbc
    nbc
    fox news
    buzzfeed
    daily mail
    cnn
    breitbart
    huffington post
    breitbartnews
    washington post
    ny times
    new york times
    facebook
    9gag
    techcrunch
    diversity
    sjw
    racial
    sexist
    cis
    racist
    feminism
    sexism
    feminist
    bigotry
    safe space
    genders
    toxic masculinity
    mansplaining
    mansplain
    misogyny
    manspreading
    mens rights
    white privilege
    white male
    white man
    white boy
    white girl
    white woman
    white women
    oppressed
    neoliberal
    white genocide
    microaggression
    oppression
    nationalist
    black man
    black men
    black guy
    black dude
    black dudes
    black woman
    black women
    black girl
    black girls
    black power
    hate speech
    asian man
    asian men
    asian guy
    asian dude
    asian woman
    asian women
    manarchism
    cisplaining
    intersexual
    intersex
    transphobic
    transphobia
    transgender
    snowflake
    cisgender
    all lives matter
    black lives matter
    blm
    racism
    hormone treatment
    hormone therapy
    privilege
    triggered
    cuck
    cucked
    activism
    gender
    queer
    lgbtq
    agesplaining
    bigender
    ageist
    ageism
    harassment
    womansplain
    white supremacy
    microaggressor
    discrimination
    ablesplaining
    white men
    vegan
    cisethnic
    equality
    bombing
    bombed
    died
    dies
    dead    
    suicide
    murder
    murders
    murderer
    shooting
    shooter
    shot
    killed
    killing
    raped
    rape
    knife attack
    stabbing
    stabbed
    covid
    coronavirus
    covid-19
    antivaxxers
    moderna
    pfizer
    mrna
    booster
    vaccine
    kpop
    btsarmy
    bts
    allkpop
    fortnite
    minecraft
    call of duty
    ActivityTweet
    generic_activity_highlights
    generic_activity_momentsbreaking
    RankedOrganicTweet
    suggest_activity
    suggest_activity_feed
    suggest_activity_highlights
    suggest_activity_tweet
    suggest_grouped_tweet_hashtag
    suggest_pyle_tweet
    suggest_ranked_organic_tweet
    suggest_ranked_timeline_tweet
    suggest_recap
    suggest_recycled_tweet
    suggest_recycled_tweet_inline
    suggest_sc_tweet
    suggest_timeline_tweet
    suggest_who_to_follow
    suggestactivitytweet
    suggestpyletweet
    suggestrecycledtweet_inline`.split(/\W+/);

    const nativeInputValueSetter = Object.getOwnPropertyDescriptor(window.HTMLInputElement.prototype, "value").set;

    const addMutedKeyword = keyword => {
      const input = document.querySelector("[name='keyword']");
      nativeInputValueSetter.call(input, keyword);
      input.dispatchEvent(new Event('input', { bubbles: true }));
      document.querySelector("[data-testid='settingsDetailSave']").click();
    }

    const delay = () => {
      return new Promise(res => setTimeout(res, delayMs));
    };

    keywords.reduce(async (prev, keyword) => {
      await prev;
      document.querySelector("a[href='/settings/add_muted_keyword']").click();
      await delay();
      addMutedKeyword(keyword);
      return delay();
    }, Promise.resolve());


