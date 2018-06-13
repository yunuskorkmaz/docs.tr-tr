---
title: 'Nasıl yapılır: Belirteç yeniden yürütme algılaması etkinleştir'
ms.date: 03/30/2017
ms.assetid: 5a9f5771-f5f6-4100-8501-406aa20d731a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b9c187998b4af41e1a56ed9a64625da7e4f95d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408066"
---
# <a name="how-to-enable-token-replay-detection"></a>Nasıl yapılır: Belirteç yeniden yürütme algılaması etkinleştir
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF)  
  
-   ASP.NET® Web formları  
  
## <a name="summary"></a>Özet  
 Bu yöntem, belirteç yeniden yürütme algılaması WIF kullanan bir ASP.NET uygulamasında etkinleştirmek için ayrıntılı adım adım yordamlar sağlar. Ayrıca, belirteç yeniden yürütme algılaması etkin olduğunu doğrulamak için uygulamayı test etme için yönergeler sağlar. Bu 'Nasıl Yapılır' konusunda bir Güvenlik Belirteci Hizmeti (STS) oluşturmaya yönelik ayrıntılı yönergeler yer almaz ve bunun yerine Kimlik ve Erişim aracı ile birlikte gelen Geliştirme STS'si kullanılır. Geliştirme STS'si gerçek kimlik doğrulaması yapmaz ve yalnızca test amaçlarına yöneliktir. Bu 'Nasıl Yapılır' konusunu tamamlamak için Kimlik ve Erişim aracını yüklemeniz gerekir. Şu konumdan indirilebilir: [kimlik ve erişim aracı](http://go.microsoft.com/fwlink/?LinkID=245849)  
  
## <a name="contents"></a>İçindekiler  
  
-   Amaçlar  
  
-   Genel Bakış  
  
-   Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve etkinleştirme yeniden yürütme algılaması  
  
-   2. adım – çözümünüzü  
  
## <a name="objectives"></a>Amaçlar  
  
-   WIF ve geliştirme STS kimlik ve erişim aracı kullanan basit bir ASP.NET uygulaması oluşturma  
  
-   Belirteç yeniden yürütme algılaması etkinleştirin ve çalışır durumda olduğunu doğrulayın  
  
## <a name="overview"></a>Genel Bakış  
 Bir istemci istemcinin zaten kullanmış olduğu bir STS belirteci ile bağlı olan taraf için kimlik doğrulaması çalıştığında yeniden gönderme saldırısı oluşur. Bu saldırı önlemeye yardımcı olmak için daha önce kullanılan STS belirteç yeniden yürütme algılama önbelleği WIF içerir. Etkinleştirildiğinde, yeniden yürütme algılaması gelen istek belirteci denetler ve belirteç daha önce kullanılan olup olmadığını doğrular. Belirteç zaten kullanılıyorsa, isteği reddetti ve <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> özel durumu oluşur.  
  
 Aşağıdaki adımlarda, yeniden yürütme algılaması etkinleştirmek için gereken yapılandırma değişikliklerini gösterilmektedir.  
  
## <a name="summary-of-steps"></a>Adımların Özeti  
  
-   1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve etkinleştirme yeniden yürütme algılaması  
  
-   2. adım – çözümünüzü  
  
## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-replay-detection"></a>1. adım – basit bir ASP.NET Web Forms uygulaması oluşturma ve etkinleştirme yeniden yürütme algılaması  
 Bu adımda, yeni bir ASP.NET Web Forms uygulaması oluşturacak ve değiştirme *Web.config* yeniden yürütme algılaması sağlamak için dosya.  
  
#### <a name="to-create-a-simple-aspnet-application"></a>Basit bir ASP.NET uygulaması oluşturmak için  
  
1.  Visual Studio'yu başlatın ve tıklatın **dosya**, **yeni**ve ardından **proje**.  
  
2.  İçinde **yeni proje** penceresinde tıklatın **ASP.NET Web Forms uygulaması**.  
  
3.  İçinde **adı**, girin `TestApp` ve basın **Tamam**.  
  
4.  Sağ **TestApp** altında proje **Çözüm Gezgini**seçeneğini belirleyip **kimlik ve erişim**.  
  
5.  **Kimlik ve erişim** penceresi görüntülenir. Altında **sağlayıcıları**seçin **yerel geliştirme STS ile uygulamanızı Test**, ardından **Uygula**.  
  
6.  Aşağıdakileri ekleyin  **\<tokenReplayDetection >** öğesine *Web.config* hemen ardından yapılandırma dosyası  **\<System.IdentityModel >** ve  **\<identityConfiguration >** gibi öğeler, gösterilen:  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration>  
            <tokenReplayDetection enabled="true"/>  
    ```  
  
## <a name="step-2--test-your-solution"></a>2. adım – çözümünüzü  
 Bu adımda, yeniden yürütme algılaması etkin olduğunu doğrulamak için WIF etkinleştirilmiş ASP.NET uygulamanızı test.  
  
#### <a name="to-test-your-wif-enabled-aspnet-application-for-replay-detection"></a>Yeniden yürütme algılaması için ASP.NET WIF özellikli uygulamanızı test etmek için  
  
1.  Tuşlarına basarak çözümü çalıştırın **F5** anahtarı. Varsayılan ASP.NET giriş sayfası ile sunulan ve gerekir otomatik olarak kullanıcı adıyla kimlik doğrulaması *Terry*, geliştirme STS tarafından döndürülen varsayılan kullanıcı olduğu.  
  
2.  Tarayıcının basın **geri** düğmesi. İle sunulan bir **'/' uygulamasında sunucu hatası** aşağıdaki açıklama sayfasıyla: *ID1062: yeniden yürütme için algılandı: belirteç: 'System.IdentityModel.Tokens.SamlSecurityToken'* , ve ardından bir *onaylama kimliği* ve bir *veren*.  
  
     Bu hata sayfası için görüyorsunuz türünde bir özel durum <xref:System.IdentityModel.Tokens.SecurityTokenReplayDetectedException> belirteç yeniden yürütme algılandığında belirtildi. Belirtecin ilk sunulduğunda ilk POST isteği yeniden göndermek denediğinizden bu hata oluşur. **Geri** düğmesi değil davranışlara neden olur bu sunucuya sonraki isteklerde.
