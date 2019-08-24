---
title: WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: 1db62f3e7d073fd1bf9bf9d4d0e17703310f2e69
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988594"
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları
Uluslararası etki alanı adlarına (ıDN) sahip WCF hizmetlerine izin vermek için destek eklenmiştir. Uluslararası bir etki alanı adı ASCII olmayan karakterler içeren bir etki alanı adıdır. Bu destek, hem ıDN adı ile bir WCF hizmetini hem de bir ıDN adıyla bir Web hizmetiyle konuşmak üzere bir WCF istemcisini barındırmanıza olanak tanır.  
  
## <a name="systemuri-and-idn"></a>System. Uri ve ıDN  
 <xref:System.Uri>iki özelliğe <xref:System.Uri.Host%2A> <xref:System.Uri.DnsSafeHost%2A>sahiptir. Bu özellikler, ıDN yapılandırma ayarlarına bağlı olarak Unicode veya Punyıcode değerlerini içerir.  
  
 IDN, bir uygulamanın yapılandırma dosyasında aşağıdaki XML kullanılarak etkinleştirildi  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 \<IDN > öğesi, aşağıdaki değerlerden birine ayarlanbilen enabled özniteliğini içerir:  
  
1. "None"  
  
2. "AllExceptIntranet"  
  
3. Bütün  
  
 IDN ayarı "none" olarak ayarlandığında, Uri. Host veya Uri. DnsSafeHost tarafından hiçbir dönüştürme yapılmaz. IDN ayarı "All", URI olarak ayarlandığında. Ana bilgisayar Unicode ve URI kalır. DnsSafeHost, Punyıcode 'a dönüştürüldü. IDN ayarı "AllExceptIntranet" olarak ayarlandığında URI. DnsSafeHost Internet adresleri için zayıf koda dönüştürülür ve intranet adresleri için Unicode olarak kalır. Bu ayar, doğru DNS ad çözümlemesi için önemlidir. Not Bu ayarın, Windows 8 ve daha yeni sürümler için yapılandırılması gerekmez.  
  
> [!WARNING]
> Punyıcode kullanarak bir adresi asla sabit bir şekilde kodmalısınız. WCF, uyguladığınız yapılandırma ayarlarına bağlı olarak bunu sizin için dönüştürür.  
  
> [!WARNING]
> ApplicationHost. exe. config dosyasına Unicode karakterler eklerken, dosyayı UTF-8 kodlamasını kullanarak kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Uri?displayProperty=nameWithType>
