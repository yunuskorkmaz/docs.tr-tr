---
title: "ServiceHostFactory Kullanarak Barındırmayı Genişletme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06859e8f12f96f964054817bac553f6534d5960e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="8d2d7-102">ServiceHostFactory Kullanarak Barındırmayı Genişletme</span><span class="sxs-lookup"><span data-stu-id="8d2d7-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="8d2d7-103">Standart <xref:System.ServiceModel.ServiceHost> Hizmetleri'nde barındırmak için API [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] bir genişletilebilirlik noktasıdır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mimarisi.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is an extensibility point in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] architecture.</span></span> <span data-ttu-id="8d2d7-104">Kullanıcılar kendi ana bilgisayar sınıftan türetilen <xref:System.ServiceModel.ServiceHost>, genellikle geçersiz kılmak için <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> kullanmak için <xref:System.ServiceModel.Description.ServiceDescription> imperatively varsayılan uç noktaları eklemek veya hizmet açmadan önce davranışları değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="8d2d7-105">Kendini barındırma ortamında bir özel Oluştur gerekmez <xref:System.ServiceModel.ServiceHost> ana bilgisayarı başlatır kodu yazın ve ardından çağırın çünkü <xref:System.ServiceModel.ICommunicationObject.Open> Bu örneği sonra üzerinde.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="8d2d7-106">Bu iki adımları arasında istediğiniz yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="8d2d7-107">Örneğin, yeni bir ekleyebilirsiniz <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="8d2d7-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="8d2d7-108">Bu yaklaşım yeniden kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-108">This approach is not reusable.</span></span> <span data-ttu-id="8d2d7-109">Açıklama işleyen kodu ana bilgisayar kodlanmış program (Bu durumda, Main() işlevi), bu mantığı diğer bağlamlarda yeniden zordur.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="8d2d7-110">Ekleme başka yolları da vardır bir <xref:System.ServiceModel.Description.IServiceBehavior> kesinlik temelli kod gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="8d2d7-111">Özniteliği türetilemeyeceğini <xref:System.ServiceModel.ServiceBehaviorAttribute> ve hizmet uygulamanızı türü veya özel bir davranış yapılandırılabilir hale getirebilir ve dinamik olarak yapılandırma kullanarak oluşturan olduğunu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="8d2d7-112">Ancak, küçük bir çeşididir Örneğin bu sorunu çözmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="8d2d7-113">Bir yaklaşım ise kullanıma ServiceBehavior ekleyen kod taşımak için `Main()` ve içine <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> özel bir türevi yöntemi <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="8d2d7-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 <span data-ttu-id="8d2d7-114">Ardından, içinde `Main()` kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8d2d7-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="8d2d7-115">Şimdi birçok farklı ana bilgisayar yürütülebilir dosyalar arasında kolayca yeniden kullanılabilir bir temiz soyutlama içine özel mantık kapsüllenmiş.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="8d2d7-116">Bu özel kullanmayı hemen göze erişilebilir <xref:System.ServiceModel.ServiceHost> gelen Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) içinde.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="8d2d7-117">Barındırma ortamı bir örneği olduğundan bu ortamlarda kendini barındırma ortamı farklı <xref:System.ServiceModel.ServiceHost> uygulama adına.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="8d2d7-118">IIS ve WAS'ta barındırma altyapı özel hakkında hiçbir şey bilmez <xref:System.ServiceModel.ServiceHost> türevi.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="8d2d7-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> Özel erişme bu sorunu çözmek için tasarlanmıştır <xref:System.ServiceModel.ServiceHost> gelen IIS ya da WAS içinde.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="8d2d7-120">Özel bir ana bilgisayar olduğundan türetilmiş <xref:System.ServiceModel.ServiceHost> dinamik olarak yapılandırılır ve potansiyel olarak çeşitli türlerde barındırma ortamı hiçbir zaman onu doğrudan başlatır.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="8d2d7-121">Bunun yerine, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yöneltme barındırma ortamı ve hizmetin somut türü arasında katmanı sağlamak için Fabrika desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-121">Instead, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="8d2d7-122">Aksi takdirde söyleyin sürece, bir varsayılan uygulaması kullanır <xref:System.ServiceModel.Activation.ServiceHostFactory> örneği döndürür <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="8d2d7-123">Ancak Fabrika uygulamanızda CLR türü adını belirterek türetilmiş ana bilgisayarınız döndürür kendi Fabrika de sağlayabilirsiniz @ServiceHost yönergesi.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="8d2d7-124">Amaç, temel durumlarda, kendi Fabrika uygulama düz iletme alıştırma olması gerektiğini ' dir.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="8d2d7-125">Örneğin, özel bir işte <xref:System.ServiceModel.Activation.ServiceHostFactory> türetilmiş döndüren <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="8d2d7-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="8d2d7-126">Bu fabrikada yerine varsayılan fabrika kullanmak için tür adı sağlayın @ServiceHost şekilde yönergesi:</span><span class="sxs-lookup"><span data-stu-id="8d2d7-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="8d2d7-127">Varken teknik sınır için istediğiniz yapmayı <xref:System.ServiceModel.ServiceHost> döndürmek, <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, Fabrika uygulamaları olabildiğince basit tutmak öneririz.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="8d2d7-128">Çok sayıda özel mantık varsa, yeniden kullanılabilir olması için bu mantığı, ana bilgisayar yerine içinde Fabrika yerleştirilecek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="8d2d7-129">Burada belirtilen barındırma API bir daha fazla katmana yoktur.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-129">There is one more layer to the hosting API that should be mentioned here.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="8d2d7-130">Ayrıca <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, içinden <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türetilir.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-130"> also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="8d2d7-131">Bu, kendi özelleştirilmiş oluşturmaları ile meta veri sistem büyük bölümlerini burada takas gerekir daha Gelişmiş senaryolar için mevcut.</span><span class="sxs-lookup"><span data-stu-id="8d2d7-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
