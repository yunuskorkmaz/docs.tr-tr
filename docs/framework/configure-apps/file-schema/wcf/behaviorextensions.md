---
description: 'Hakkında daha fazla bilgi edinin: <behaviorExtensions>'
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: 0bd641f8e26d309c592c07bcc19ff02897fe71cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639529"
---
# \<behaviorExtensions>

<span data-ttu-id="06b58-102">Davranış uzantıları, kullanıcının Kullanıcı tanımlı davranış öğeleri oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="06b58-102">Behavior extensions enable the user to create user-defined behavior elements.</span></span> <span data-ttu-id="06b58-103">Bu öğeler, standart Windows Communication Foundation (WCF) davranış öğelerinden daha fazla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06b58-103">These elements can be used alongside the standard Windows Communication Foundation (WCF) behavior elements.</span></span> <span data-ttu-id="06b58-104">`behaviorExtensions`Bölümü, öğesini yapılandırmada kullanılabilecek şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06b58-104">The `behaviorExtensions` section defines the element such that it can be used in configuration.</span></span> <span data-ttu-id="06b58-105">Tipik bir davranış uzantısının örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="06b58-105">Here is an example of a typical behavior extension.</span></span>  
  
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
  
 <span data-ttu-id="06b58-106">Öğeye yapılandırma becerileri eklemek için bir yapılandırma öğesi yazmanız ve kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="06b58-106">To add configuration abilities to the element, you need to write and register a configuration element.</span></span> <span data-ttu-id="06b58-107">Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="06b58-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="06b58-108">Öğesi ve yapılandırma türü tanımlandıktan sonra, aşağıdaki örnekte gösterildiği gibi uzantı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="06b58-108">After the element and its configuration type are defined, the extension can be used, as shown in the following example.</span></span>  
  
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
  
## <a name="security"></a><span data-ttu-id="06b58-109">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="06b58-109">Security</span></span>  

 <span data-ttu-id="06b58-110">Ve dosyalarına türleri kaydederken tam nitelikli derleme adlarını kullanmanız önemle tavsiye edilir `machine.config` `app.config` .</span><span class="sxs-lookup"><span data-stu-id="06b58-110">It is strongly recommended that you use fully qualified assembly names when registering types in the `machine.config` and `app.config` files.</span></span> <span data-ttu-id="06b58-111">Tür benzersiz olarak tanımlanmamışsa CLR tür yükleyicisi, belirtilen sırada aşağıdaki konumlarda bunu arar:</span><span class="sxs-lookup"><span data-stu-id="06b58-111">If the type is not uniquely defined, the CLR type loader searches for it in the following locations in the specified order:</span></span>  
  
 <span data-ttu-id="06b58-112">Türün derlemesi biliniyorsa, yükleyici yapılandırma dosyasının yeniden yönlendirme konumlarını, GAC 'yi, yapılandırma bilgilerini kullanarak geçerli derlemeyi ve uygulama temel dizinini arar.</span><span class="sxs-lookup"><span data-stu-id="06b58-112">If the assembly of the type is known, the loader searches the configuration file's redirect locations, GAC, the current assembly using configuration information, and the application base directory.</span></span> <span data-ttu-id="06b58-113">Derleme bilinmiyorsa, yükleyici geçerli derlemeyi, mscorlib 'yi ve olay işleyicisi tarafından döndürülen konumu arar `TypeResolve` .</span><span class="sxs-lookup"><span data-stu-id="06b58-113">If the assembly is unknown, the loader searches the current assembly, mscorlib, and the location returned by the `TypeResolve` event handler.</span></span> <span data-ttu-id="06b58-114">Bu CLR arama sırası tür Iletme mekanizması ve AppDomain. TypeResolve Event gibi kancalar ile değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="06b58-114">This CLR search order can be modified with hooks such as the Type Forwarding mechanism and the AppDomain.TypeResolve event.</span></span>  
  
 <span data-ttu-id="06b58-115">Bir saldırgan CLR arama siparişinden yararlanabilir ve yetkisiz kod yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="06b58-115">An attacker can exploit the CLR search order and execute unauthorized code.</span></span> <span data-ttu-id="06b58-116">Tam nitelikli (tanımlayıcı) adların kullanılması, bir türü benzersiz bir şekilde tanımlar ve sisteminizin güvenliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="06b58-116">Using fully qualified (strong) names uniquely identifies a type and further increases security of your system.</span></span>  
  
 <span data-ttu-id="06b58-117">Daha fazla bilgi için bkz. [çalışma zamanı derlemeleri ve öğesini nasıl konumlandırır](../../../deployment/how-the-runtime-locates-assemblies.md) <xref:System.AppDomain.TypeResolve> .</span><span class="sxs-lookup"><span data-stu-id="06b58-117">For more information, see [How the Runtime Locates Assemblies](../../../deployment/how-the-runtime-locates-assemblies.md) and <xref:System.AppDomain.TypeResolve>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b58-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06b58-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [<span data-ttu-id="06b58-119">Çalışma Zamanını Davranışlarla Yapılandırma ve Genişletme</span><span class="sxs-lookup"><span data-stu-id="06b58-119">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
