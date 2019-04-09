---
title: WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları
ms.date: 03/30/2017
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
ms.openlocfilehash: c166f497117314dd8cea3b04b9b1072203374c52
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112612"
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları
WCF hizmetleri Uluslararası yapılan etki alanı adı (IDN) ile izin vermek için destek eklendi. Bir Uluslararası yapılan etki alanı adı, ASCII olmayan karakterler içeren bir etki alanı adı değil. Bir WCF istemcisi IDN adı ile bir web hizmeti konuşabilir bir IDN adı ile bir WCF Hizmeti barındırma her iki özelliği destekler.  
  
## <a name="systemuri-and-idn"></a>System.Uri ve IDN  
 <xref:System.Uri> iki özelliğe sahiptir <xref:System.Uri.Host%2A> ve <xref:System.Uri.DnsSafeHost%2A>. Bu özellikler, IDN yapılandırma ayarlarına bağlı olarak, Unicode veya Punycode değerleri içerir.  
  
 Bir uygulamanın yapılandırma dosyasında aşağıdaki XML kullanarak IDN etkin  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 \<IDN > öğesi içerir etkin özniteliği şu değerlerden birine ayarlayın:  
  
1.  "None"  
  
2.  "AllExceptIntranet"  
  
3.  "Tüm"  
  
 IDN ayarını "Yok" olarak ayarlandığında, hiçbir dönüştürmeler Uri.Host veya Uri.DnsSafeHost tarafından gerçekleştirilir. Ne zaman IDN ayarı "Tümü", URI ayarlanır. Konak, Unicode ve URI kalır. DnsSafeHost kodlar, zayıf koda dönüştürülür. Ne zaman IDN ayarı "AllExceptIntranet için", URI ayarlanır. DnsSafeHost internet adresleri için kodlar, zayıf koda dönüştürülür ve Unicode için intranet adresleri kalır. Bu ayar, doğru DNS ad çözümlemesi için önemlidir. Bu ayar Windows 8 ve daha yeni sürümleri için yapılandırılması için gerekli olmayan unutmayın.  
  
> [!WARNING]
>  Hiçbir sabit kodlu gereken zayıf kod kullanarak bir adres. WCF uyguladığınız yapılandırma ayarlarına göre bunu dönüştürür.  
  
> [!WARNING]
>  Unicode karakterler için applicationHost.exe.config eklerken, UTF-8 kodlaması kullanarak dosyayı kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Uri?displayProperty=nameWithType>
