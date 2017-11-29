---
title: "WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8a3e10a-8bc2-4a78-8d86-a562ba6e65fa
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ab9346e7826fcef5151ef976b6ca7f25120fa5a3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-and-internationalized-domain-names"></a>WCF ve Uluslararası Hale Getirilmiş Etki Alanı Adları
WCF hizmetleri Uluslararası yapılan etki alanı adları (IDN) ile izin vermek için destek eklenmiştir. Uluslararası etki alanı ASCII olmayan karakterler içeren bir etki alanı adıdır. Bu destek bir IDN adı ve bir web hizmetini bir IDN adı ile iletişim kuran bir WCF istemcisi ile WCF Hizmeti barındırma her iki özelliği içerir.  
  
## <a name="systemuri-and-idn"></a>System.Uri ve IDN  
 <xref:System.Uri>iki özelliğe sahip <xref:System.Uri.Host%2A> ve <xref:System.Uri.DnsSafeHost%2A>. Bu özellikleri IDN yapılandırma ayarlarına bağlı olarak Unicode ya da Punycode değerlerini içerir.  
  
 Bir uygulamanın yapılandırma dosyasında aşağıdaki XML kullanarak IDN etkin  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All/AllExceptIntranet/None" />  
  </uri>  
</configuration>  
```  
  
 \<IDN > öğesi içeriyor etkin özniteliği aşağıdaki değerlerden birine ayarlayın:  
  
1.  "Hiçbiri"  
  
2.  "AllExceptIntranet"  
  
3.  "Tümü"  
  
 IDN ayarını "Yok" olarak ayarlandığında, hiçbir dönüşümleri Uri.Host veya Uri.DnsSafeHost tarafından gerçekleştirilir. Ne zaman IDN ayarı "Tümü", URI ayarlanır. Ana bilgisayar Unicode ve URI kalır. DnsSafeHost kodlar, zayıf koda dönüştürülür. Ne zaman IDN ayarı "AllExceptIntranet için", URI ayarlanır. DnsSafeHost internet adresleri için kodlar, zayıf koda dönüştürülür ve intranet adresleri için Unicode kalır. Bu ayar, doğru DNS ad çözümlemesi için önemlidir. Bu ayar Windows 8 ve daha yeni sürümleri için yapılandırılması için gerekli olmayan unutmayın.  
  
> [!WARNING]
>  Hiçbir sabit kodlu gereken zayıf kod kullanarak bir adres. WCF, uyguladığınız yapılandırma ayarlarınızı temel alan grafiği dönüştürür.  
  
> [!WARNING]
>  Unicode karakterler için applicationHost.exe.config eklerken, UTF-8 kodlaması kullanarak dosyayı kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [System.Uri](http://msdn.microsoft.com/library/system.uri.aspx)
