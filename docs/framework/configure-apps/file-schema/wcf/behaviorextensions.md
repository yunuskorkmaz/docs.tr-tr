---
title: '&lt;behaviorExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed7c75fb7070b43b850a8f5b812abf0a52c3c16f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yapılandırma ve çalışma zamanını davranışlarla genişletme](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
