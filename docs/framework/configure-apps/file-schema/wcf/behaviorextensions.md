---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 39dc92d65a41d223ebd39aec3dc59871ad1fd101
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77448691"
---
# \<behaviorExtensions>
Davranış uzantıları, kullanıcının Kullanıcı tanımlı davranış öğeleri oluşturmasını sağlar. Bu öğeler, standart Windows Communication Foundation (WCF) davranış öğelerinden daha fazla kullanılabilir. `behaviorExtensions`Bölümü, öğesini yapılandırmada kullanılabilecek şekilde tanımlar. Tipik bir davranış uzantısının örneği aşağıda verilmiştir.  
  
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
  
 Öğeye yapılandırma becerileri eklemek için bir yapılandırma öğesi yazmanız ve kaydetmeniz gerekir. Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .  
  
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
 Ve dosyalarına türleri kaydederken tam nitelikli derleme adlarını kullanmanız önemle tavsiye edilir `machine.config` `app.config` . Tür benzersiz olarak tanımlanmamışsa CLR tür yükleyicisi, belirtilen sırada aşağıdaki konumlarda bunu arar:  
  
 Türün derlemesi biliniyorsa, yükleyici yapılandırma dosyasının yeniden yönlendirme konumlarını, GAC 'yi, yapılandırma bilgilerini kullanarak geçerli derlemeyi ve uygulama temel dizinini arar. Derleme bilinmiyorsa, yükleyici geçerli derlemeyi, mscorlib 'yi ve olay işleyicisi tarafından döndürülen konumu arar `TypeResolve` . Bu CLR arama sırası tür Iletme mekanizması ve AppDomain. TypeResolve Event gibi kancalar ile değiştirilebilir.  
  
 Bir saldırgan CLR arama siparişinden yararlanabilir ve yetkisiz kod yürütebilir. Tam nitelikli (tanımlayıcı) adların kullanılması, bir türü benzersiz bir şekilde tanımlar ve sisteminizin güvenliğini artırır.  
  
 Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri ve öğesini nasıl konumlandırır](../../../deployment/how-the-runtime-locates-assemblies.md) <xref:System.AppDomain.TypeResolve> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
