# Dmitry Semenov #
## dmitry_proekt@mail.ru ##
## +7 926 320 37 83 ##

**Summary**:

Dream of working as a programmer since *school time*, but after graduation enter the MEPHI institute for the specialty of electronics development. 

After graduation from institute **start a business** (online store) and sell playing cards, magic tricks and poker sets all over the Russian Federation **for 10 years**. During this, working on the store website and fall in love with web development. 

In the 2018th start to **study Web Developer profession** from http://geekbrains.ru courses, and in the 2019th, after graduated from courses, **in a one week** find my first job in IT as *PHP Developer* in marketing agency located in Moscow. At the moment working here for *7 months* developing sites and CRMs on Yii2 framework for **Procter & Gamble**, **Volkswagen** and **BMW** brands.

Really like backend, but at work also often have to deal with different frontend techs – CSS, JS etc. Very interested in upgrade my skills in frontend, studying modern frontend technologies (like SPA with ReactJS). Dream of becoming a *fullstack developer*.

**Skills**:

*Languages/frameworks*: PHP7.2, Yii2, Codeception, Laravel 5, JavaScript (ES6), jQuery
*DBs*: MySQL, PostgreSQL
*APIs*: Facebook Graph, Vkontakte, Russian Post, Janrain, StrikeIron, Google Measurement Protocol, SMS-Prosto API
*Utils*: Sentry, PHPStorm, WebStorm, VSCode, OpenServer, Ampps
*Some techs*: AJAX, JSON, Http, Vagrant, Composer
*Version control*: Git, Gitlab CI/CD
*Development methodologies*: SOLID, SCRUM

**Code Example** (email validator, php):

```php
class EmailBlackListsValidator extends Validator
{
    public function validateAttribute($model, $attribute)
    {
        if(strpos($model->$attribute, '+') !== false){
            $this->addError($model, $attribute, 'В E-mail не допускается использование символа «+». Пожалуйста, исправьте?');
        }
    
        $emailDomain =  explode('@', $model->$attribute)[1];

        // по новому ТЗ от 03-12-2019 - Если (хотя бы один [элемент] справочника «Blacklist домен (часть)» содержится в [E-mail] как [E-mail] LIKE ‘%@%[элемент]’
        if(
            BlackListDomains::find()->where(['domain' => strtolower($emailDomain)])->exists()
            || BlackListDomainsPart::find()->where(new \yii\db\Expression(":email LIKE CONCAT('%@%', part)", ['email' => $model->$attribute,]))->exists()
            || BlackListEmails::find()->where(['email' => strtolower($model->$attribute)])->exists()
        )
            {
            $this->addError($model, $attribute, 'К сожалению, мы не можем зарегистрировать данный e-mail. Пожалуйста, укажите другой адрес.');
        }
    }
}
```

**Experience**:

* integrate my online store’s CMS (PHPShop) with sms service (SMS-Prosto) to send sms messages on order status’ changing,
* integrate my online store’s CMS with Russian Post service to daily update customers orders’ tracking information,
* integrate company’s internal CRM with Facebook Graph API to receive leads from Facebook,
* integrate company’s internal CRM with Vkontakte API to receive leads from Vkontakte,
* developing more than 20 modules (sites on global platform) for Procter & Gamble’s promo actions.
