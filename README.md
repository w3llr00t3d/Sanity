# Sanity
Maintain sanity on the bird app

Automation:
Visit https://twitter.com/settings/muted_keywords
Open your browser's dev tools (note: this does work in Chrome)
Paste the following code in: (note you may have to clear your existing mute list first)

    const delayMs = 500; // change this if you feel like its running too fast

    const keywords = `elon
    el0n
    musk
    elno
    mastodon
    political
    politics
    trump
    donald
    covfefe
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
    democrat
    republicans
    cuckservatives
    trudeau
    merkel
    republican
    trumpism
    leftist
    rnc
    dnc
    obamacare
    senator
    hillary
    macron
    obama
    clinton
    erdogan
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
    msnbc
    nbc
    buzzfeed
    cnn
    breitbart
    breitbartnews
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
    genders
    mansplaining
    mansplain
    misogyny
    manspreading
    oppressed
    neoliberal
    microaggression
    oppression
    nationalist
    manarchism
    cisplaining
    intersexual
    intersex
    transphobic
    transphobia
    transgender
    snowflake
    cisgender
    blm
    racism
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
    microaggressor
    discrimination
    ablesplaining
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


