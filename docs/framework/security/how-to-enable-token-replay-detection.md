---
title: 'Nasıl yapılır: Belirteç yeniden yürütme algılamayı etkinleştirme'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: dd5adf39c37fce92d4caf1d85e2a6a12e9e6b59b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486522"
---
# <a name="how-to-enable-token-replay-detection"></a>Nasıl yapılır: Belirteç yeniden yürütme algılamayı etkinleştirme
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu nasıl yapılır, WIF kullanan ASP.NET uygulamasında belirteç yeniden yürütme algılaması etkinleştirmek için adım adım ayrıntılı yordamları sağlar. Ayrıca, belirteç yeniden yürütme algılaması etkin olduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Şu konumdan indirilebilir: [kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturun ve yeniden yürütme algılamayı etkinleştirme  
  
-   2. adım – çözümünüzü test etme  
  
## <a name="objectives"></a>Amaçlar  
  
-   WIF ve kimlik ve erişim aracı geliştirme STS'sini kullanan basit bir ASP.NET uygulaması oluşturma  
  
-   Belirteç yeniden yürütme algılamayı etkinleştirme ve çalışır durumda olduğunu doğrulayın  
  
## <a name="overview"></a>Genel Bakış  
 Yeniden yürütme saldırı, bir istemci istemcinin zaten kullanmış olduğu bir STS belirteci ile bağlı olan taraf için kimlik doğrulama girişiminde bulunduğunda oluşur. Bu saldırı önlemeye yardımcı olmak için önceden kullanılmış STS belirteç yeniden yürütme algılama önbelleğini WIF içerir. Etkin olduğunda, yeniden yürütme algılaması gelen istek belirtecini denetler ve belirteci daha önce kullanılan olup olmadığını doğrular. Belirteç zaten kullanılıyor, istek reddedildi ve <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> özel durumu oluşturulur.  
  
 Aşağıdaki adımlarda, yeniden yürütme algılamayı etkinleştirmek için gereken yapılandırma değişikliklerini gösterilmektedir.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturun ve yeniden yürütme algılamayı etkinleştirme  
  
-   2. adım – çözümünüzü test etme  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturun ve yeniden yürütme algılamayı etkinleştirme  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve değiştirme *Web.config* yeniden yürütme algılamayı etkinleştirmek için dosya.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklayın **dosya**, **yeni**, ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklayın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` basın **Tamam**.  
  
4.  Sağ **TestApp** altındaki proje **Çözüm Gezgini**, ardından **kimlik ve erişim**.  
  
5.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **uygulamanızı yerel geliştirme STS'si ile Test**, ardından **Uygula**.  
  
6.  Aşağıdaki  **\<tokenReplayDetection >** öğesine *Web.config* hemen yapılandırma dosyası  **\<System.IdentityModel >** ve  **\<identityConfiguration >** gibi öğeler, gösterilen:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>2. adım – çözümünüzü test etme  
 Bu adımda, WIF özelliği etkinleştirilmiş ASP.NET uygulamanızı yeniden yürütme algılaması etkin olduğunu doğrulamak için test eder.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Yeniden yürütme algılaması için WIF özelliği etkinleştirilmiş ASP.NET uygulamanızı test etmek için  
  
1.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı. Verilecek varsayılan ASP.NET ana sayfası gösterilir ve otomatik olarak kullanıcı adıyla kimlik doğrulaması *Terry*, geliştirme STS tarafından döndürülen varsayılan kullanıcı olduğu.  
  
2.  Tarayıcının basın **geri** düğmesi. İle sunulan bir **'/' uygulamasında sunucu hatası** aşağıdaki açıklama sayfasıyla: *ID1062: yeniden yürütme için algılandı: belirteç: 'System.IdentityModel.Tokens.SamlSecurityToken'* , ardından bir *onaylama kimliği* ve *veren*.  
  
     Bu hata sayfası için görüyorsunuz türünde bir özel durum <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> belirteç yeniden yürütme algılandığında oluşturuldu. Belirtecin ilk yansıtılırken ilk POST isteği yeniden göndermek denediğinizden bu hata oluşur. **Geri** düğmesi değil neden bu davranışı sunucuya sonraki isteklerde.
