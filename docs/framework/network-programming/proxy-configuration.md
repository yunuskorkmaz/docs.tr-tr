---
title: Proxy yapılandırması
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- adaptive proxies
- static proxies
- Network Resources
- Internet, proxy configuration
- proxies
- network, proxy configuration
- proxies, configuring
ms.assetid: 353c0a8b-4cee-44f6-8e65-60e286743df9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 41e1dcee90531de605b6bddc1eedc1c44235d8eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="proxy-configuration"></a>Proxy yapılandırması
Bir proxy sunucu kaynakları için istemci isteklerini işler. Bir proxy, istenen kaynak, önbellekten döndürür veya kaynağının bulunduğu sunucu isteği iletin. Proxy'leri uzak sunuculara gönderilen isteklerin sayısını azaltarak ağ performansını iyileştirebilir. Proxy'leri kaynaklara erişimi kısıtlamak için de kullanılabilir.  
  
## <a name="adaptive-proxies"></a>Uyarlamalı proxy'leri  
 .NET Framework'teki proxy'leri iki çeşit olarak bulunur: Uyarlamalı ve statik. Ağ yapılandırma değiştiğinde Uyarlamalı proxy'leri ayarlarına ayarlayın. Örneğin, bir dizüstü bilgisayar kullanıcı bir çevirmeli ağ bağlantısı başlarsa, Uyarlamalı proxy bu değişikliği algılar, bulmak ve kendi yeni yapılandırma komut dosyasını çalıştırın ve kendi ayarlarını uygun şekilde.  
  
 Uyarlamalı proxy'leri yapılandırma komut dosyası tarafından yapılandırılır (bkz [Otomatik Proxy algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)). Komut dosyasını bir dizi uygulama protokolleri ve her protokol için bir proxy oluşturur.  
  
 Çeşitli seçenekler yapılandırma komut dosyası çalışma şeklini denetler. Şunları belirtebilirsiniz:  
  
-   Ne sıklıkta yapılandırma komut dosyası karşıdan çalıştırın ve.  
  
-   Karşıdan yüklemek komut dosyası için beklenecek süreyi.  
  
-   Hangi sisteminizi kimlik bilgileri proxy sunucusuna erişmek için kullanmanız gerekir.  
  
-   Hangi sisteminizi kimlik bilgileri yapılandırma betiğini indir için kullanmanız gerekir.  
  
 Ağ ortamında değişiklikleri sistem proxy'leri yeni bir dizi kullanmanızı gerektirebilir. Bir ağ bağlantısı arıza ya da yeni bir ağ bağlantısı başlatıldı, sistem yeni ortamındaki yapılandırma komut dosyası, uygun kaynak bulmak ve yeni komut dosyasını çalıştırın.  
  
 Aşağıdaki tabloda, Uyarlamalı proxy için yapılandırma seçeneklerini gösterir.  
  
|Öznitelik, özellik veya yapılandırma dosyası ayarı|Açıklama|  
|--------------------------------------------------------|-----------------|  
|`scriptDownloadInterval`|Komut dosyası indirmeler arasındaki saniye cinsinden geçen süre.|  
|`scriptDownloadTimeout`|(Saniye cinsinden) indirmek komut dosyası için beklenecek süre.|  
|`useDefaultCredentials` Veya <xref:System.Net.WebProxy.UseDefaultCredentials>|Sistem bir proxy sunucusuna erişmek için varsayılan ağ kimlik bilgilerini kullanıp kullanmadığını denetler.|  
|`useDefaultCredentialForScriptDownload`|Sistem yapılandırma komut dosyasını indirmek için varsayılan ağ kimlik bilgilerini kullanıp kullanmadığını denetler.|  
|`usesystemdefaults`|(Proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini kullanıcı için Internet Explorer proxy ayarlarını okunmasına denetler. Bu değer "true", sonra statik proxy ayarlarını Internet Explorer'dan ayarlanmışsa kullanılır.<br /><br /> Bu değer ise "false" veya değil kümesi ve statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarları geçersiz kılar. Bu değer ayrıca "false" veya etkinleştirilecek Uyarlamalı proxy'leri için ayarlanmadı ayarlanması gerekir.|  
  
 Aşağıdaki örnek tipik Uyarlamalı proxy yapılandırmasını gösterir.  
  
```xml  
<system.net>  
    <defaultProxy>  
      <proxy  scriptDownloadInterval="600"  
              scriptDownloadTimeout="30"  
              useDefaultCredentials="true"  
              usesystemdefaults="true"  
      />  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="static-proxies"></a>Statik proxy'leri  
 Statik proxy'leri genellikle açıkça bir uygulama tarafından veya bir yapılandırma dosyası bir uygulama veya sistem tarafından çağrıldığında yapılandırılır. Statik proxy'leri içinde topoloji, bir kurumsal ağa bağlı bir masaüstü bilgisayar gibi sık değişmeyen ağlarda faydalıdır.  
  
 Çeşitli seçenekler statik proxy nasıl çalıştığını denetler. Şunları belirtebilirsiniz:  
  
-   Proxy adresi.  
  
-   Proxy yerel adresler için atlanmasına.  
  
-   Proxy adresleri kümesini için atlanmasına.  
  
 Aşağıdaki tabloda statik bir proxy sunucu için yapılandırma seçeneklerini gösterir.  
  
|Öznitelik, özellik veya yapılandırma dosyası ayarı|Açıklama|  
|--------------------------------------------------------|-----------------|  
|`proxyaddress` Veya <xref:System.Net.WebProxy.Address>|Kullanılacak proxy adresi.|  
|`bypassonlocal` Veya <xref:System.Net.WebProxy.BypassProxyOnLocal>|Yerel adresler için proxy atlanır olup olmadığını denetler.|  
|`bypasslist` Veya <xref:System.Net.WebProxy.BypassArrayList>|, Normal ifadelerle bir proxy atlama adresi açıklar.|  
|`usesystemdefaults`|(Proxy adresi atlama listesine ve yerel atlama) statik proxy ayarlarını gerekip gerekmediğini kullanıcı için Internet Explorer proxy ayarlarını okunmasına denetler. Bu değer "true", sonra statik proxy ayarlarını Internet Explorer'dan ayarlanmışsa kullanılır. .NET Framework bu değer "true", Internet Explorer proxy ayarları diğer proxy ayarlarını yapılandırma dosyasındaki tarafından geçersiz kılınmaz ayarlandığında 2.0. .NET Framework 1.1, Internet Explorer proxy ayarlarını diğer proxy ayarlarını yapılandırma dosyasında geçersiz kılınabilir.<br /><br /> Bu değer ise "false" veya değil kümesi ve statik proxy ayarlarını yapılandırmada belirtilen ve Internet Explorer proxy ayarları geçersiz kılar. Bu değer ayrıca "false" veya etkinleştirilecek Uyarlamalı proxy'leri için ayarlanmadı ayarlanması gerekir.|  
  
 Aşağıdaki örnek bir genel statik proxy yapılandırmasını gösterir.  
  
```xml  
<system.net>  
    <defaultProxy>  
        <proxy  proxyaddress="http://proxy.contoso.com:3128"  
                bypassonlocal="true"  
        />  
        <bypasslist>  
            <add address="[a-z]+.blueyonderairlines.com$" />  
        </bypasslist>  
    </defaultProxy>  
</system.net>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Net.WebProxy>  
 <xref:System.Net.GlobalProxySelection>  
 [Otomatik Ara Sunucu Algılama](../../../docs/framework/network-programming/automatic-proxy-detection.md)
