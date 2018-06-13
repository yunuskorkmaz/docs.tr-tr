---
title: '&lt;behaviorExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bb59ceeb478d0324fddc98a206a00dbd170b5ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749588"
---
# <a name="ltbehaviorextensionsgt"></a>&lt;behaviorExtensions&gt;
Kullanıcı tanımlı davranış öğeleri oluşturmak kullanıcı davranışı uzantıları sağlar. Standart Windows Communication Foundation (WCF) davranışı öğeleri yanı sıra bu öğeler kullanılabilir. `behaviorExtensions` Bölümü sağlayacak şekilde yapılandırmada kullanılan öğe tanımlar. Tipik davranış uzantısı bir örneği burada verilmiştir.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="myBehavior" type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
       </behaviorExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Yapılandırma yeteneklerini öğesine eklemek için yazma ve yapılandırma öğesi kaydetmeniz gerekir. Bunun hakkında daha fazla bilgi için bkz: <xref:System.Configuration> belgeleri.  
  
 Öğesini ve kendi yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi kullanılabilir.  
  
```xml  
<behaviors>  
    <behavior configurationName="testChannelBehavior">  
        <myBehavior />  
        <channelSecurity cacheCookies="false" detectReplays="false" maxCachedNonces="9"  
            maxClockSkew="00:00:03" maxCookieCachingTime="00:07:24" replayWindow="00:07:22.2190000" />  
    </behavior>  
</behaviors>  
```  
  
## <a name="security"></a>Güvenlik  
 Tam nitelikli derleme adları türlerinde kaydederken kullanmanız önemle tavsiye edilir `machine.config` ve `app.config` dosyaları. Türü benzersiz olarak tanımlanmazsa, CLR türü Yükleyicisi için belirtilen sırayla aşağıdaki konumlarda arar:  
  
 Derleme türü bilinen, yükleyici yapılandırma dosyanın yeniden yönlendirme konumları, GAC, yapılandırma bilgilerini ve uygulamanın ana dizin kullanılarak geçerli derleme arar. Derleme bilinmiyorsa, yükleyici geçerli derleme, mscorlib ve tarafından döndürülen konumu arar `TypeResolve` olay işleyicisi. Tür iletme mekanizması ve AppDomain.TypeResolve olay gibi kancaları ile bu CLR arama sırası değiştirilebilir.  
  
 Bir saldırgan, CLR arama sırası yararlanma ve yetkisiz kodunu yürütün. Tam (tanımlayıcı) adlarının benzersiz olarak kullanarak bir türü tanımlar ve daha da sisteminizin güvenliğini artırır.  
  
 Daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](http://go.microsoft.com/fwlink/?LinkId=95336) ve <xref:System.AppDomain.TypeResolve>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>  
 [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
