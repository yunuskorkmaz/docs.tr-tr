---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: bcf1f1dcdba50c3e7fba8eb170132d0cf47c4271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919815"
---
# <a name="behaviorextensions"></a>\<behaviorExtensions >
Davranış uzantıları, kullanıcının Kullanıcı tanımlı davranış öğeleri oluşturmasını sağlar. Bu öğeler, standart Windows Communication Foundation (WCF) davranış öğelerinden daha fazla kullanılabilir. `behaviorExtensions` Bölümü, öğesini yapılandırmada kullanılabilecek şekilde tanımlar. Tipik bir davranış uzantısının örneği aşağıda verilmiştir.  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Öğeye yapılandırma becerileri eklemek için bir yapılandırma öğesi yazmanız ve kaydetmeniz gerekir. Bunun hakkında daha fazla bilgi için <xref:System.Configuration> belgelerine bakın.  
  
 Öğesi ve yapılandırma türü tanımlandıktan sonra, aşağıdaki örnekte gösterildiği gibi uzantı kullanılabilir.  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>Güvenlik  
 `machine.config` Ve`app.config` dosyalarına türleri kaydederken tam nitelikli derleme adlarını kullanmanız önemle tavsiye edilir. Tür benzersiz olarak tanımlanmamışsa CLR tür yükleyicisi, belirtilen sırada aşağıdaki konumlarda bunu arar:  
  
 Türün derlemesi biliniyorsa, yükleyici yapılandırma dosyasının yeniden yönlendirme konumlarını, GAC 'yi, yapılandırma bilgilerini kullanarak geçerli derlemeyi ve uygulama temel dizinini arar. Derleme bilinmiyorsa, yükleyici geçerli derlemeyi, mscorlib 'yi ve `TypeResolve` olay işleyicisi tarafından döndürülen konumu arar. Bu CLR arama sırası tür Iletme mekanizması ve AppDomain. TypeResolve Event gibi kancalar ile değiştirilebilir.  
  
 Bir saldırgan CLR arama siparişinden yararlanabilir ve yetkisiz kod yürütebilir. Tam nitelikli (tanımlayıcı) adların kullanılması, bir türü benzersiz bir şekilde tanımlar ve sisteminizin güvenliğini artırır.  
  
 Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri](https://go.microsoft.com/fwlink/?LinkId=95336) ve <xref:System.AppDomain.TypeResolve>öğesini nasıl konumlandırır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
