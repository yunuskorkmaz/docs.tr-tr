---
title: ServiceHostFactory Kullanarak Barındırmayı Genişletme
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991321"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="c0a70-102">ServiceHostFactory Kullanarak Barındırmayı Genişletme</span><span class="sxs-lookup"><span data-stu-id="c0a70-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="c0a70-103">Standart <xref:System.ServiceModel.ServiceHost> Windows Communication Foundation (WCF) hizmetlerini barındırma API'si, WCF mimarisinin bir genişletilebilirlik noktası.</span><span class="sxs-lookup"><span data-stu-id="c0a70-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="c0a70-104">Kullanıcılar, kendi ana bilgisayar sınıflarından türetilebilir <xref:System.ServiceModel.ServiceHost>, genellikle geçersiz kılmak için <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> kullanılacak <xref:System.ServiceModel.Description.ServiceDescription> kesin varsayılan uç noktalarını eklemek veya hizmet açmadan önce davranışları değiştirmek için.</span><span class="sxs-lookup"><span data-stu-id="c0a70-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="c0a70-105">Barındırma ortamında bir özel Oluştur gerekmez <xref:System.ServiceModel.ServiceHost> konak başlatan kodu yazın ve ardından çağırmak için <xref:System.ServiceModel.ICommunicationObject.Open> sonra bu örneği üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c0a70-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="c0a70-106">Bu iki adımı arasında istediğiniz yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c0a70-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="c0a70-107">Örneğin, yeni bir ekleme olabilir <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="c0a70-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="c0a70-108">Bu yaklaşım, yeniden kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="c0a70-108">This approach is not reusable.</span></span> <span data-ttu-id="c0a70-109">Açıklama işleyen kod, ana bilgisayar kodlanmış program (Bu durumda, Main() işlevi), diğer bağlamlarda bu mantığı yeniden zor olur.</span><span class="sxs-lookup"><span data-stu-id="c0a70-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="c0a70-110">Eklemenin başka yolları da vardır bir <xref:System.ServiceModel.Description.IServiceBehavior> kesinlik temelli kod gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="c0a70-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="c0a70-111">Bir öznitelik alma türetebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> ve hizmet uygulamanızı türü veya özel bir davranış yapılandırılabilir hale getirebilir ve onu yapılandırma kullanılarak dinamik olarak oluşturmak, yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c0a70-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="c0a70-112">Bununla birlikte, küçük bir değişim Örneğin bu sorunu çözmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0a70-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="c0a70-113">Bir yaklaşım ise tanesi ServiceBehavior ekler kodu taşımak için `Main()` ve <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemi bir özel türevi <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="c0a70-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
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
  
 <span data-ttu-id="c0a70-114">Ardından, içinde `Main()` kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c0a70-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="c0a70-115">Artık birçok farklı bir konak yürütülebilir dosyalar arasında kolayca yeniden kullanılabilir bir temiz soyutlama uygulamasına özel mantığı kapsüllenmiş.</span><span class="sxs-lookup"><span data-stu-id="c0a70-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="c0a70-116">Bu özel kullanmaya nasıl hemen açık değilse <xref:System.ServiceModel.ServiceHost> gelen Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) içinde.</span><span class="sxs-lookup"><span data-stu-id="c0a70-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="c0a70-117">Barındırma ortamı bir örnekleme olduğundan bu ortamlarda barındırma ortamı farklı <xref:System.ServiceModel.ServiceHost> uygulama adına.</span><span class="sxs-lookup"><span data-stu-id="c0a70-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="c0a70-118">IIS ve WAS'ta barındırma altyapısını kendi özel hakkında hiçbir şey bilmez <xref:System.ServiceModel.ServiceHost> Türev.</span><span class="sxs-lookup"><span data-stu-id="c0a70-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="c0a70-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> Özel erişim bu sorunu çözmek için tasarlanmış <xref:System.ServiceModel.ServiceHost> dan IIS ya da WAS içinde.</span><span class="sxs-lookup"><span data-stu-id="c0a70-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="c0a70-120">Özel bir konak olmadığından türetilir <xref:System.ServiceModel.ServiceHost> dinamik olarak yapılandırılır ve potansiyel olarak çeşitli türleri, barındırma ortamı hiçbir zaman doğrudan örneğini oluşturduğunda.</span><span class="sxs-lookup"><span data-stu-id="c0a70-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="c0a70-121">Bunun yerine, WCF, barındırma ortamı ve hizmetin somut türü arasında bir yöneltme katman sağlamak için bir Fabrika deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0a70-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="c0a70-122">Aksi takdirde söyleyin sürece, varsayılan bir uygulama kullanır. <xref:System.ServiceModel.Activation.ServiceHostFactory> örneğini döndüren <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c0a70-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="c0a70-123">Ancak türetilmiş ana bilgisayar üreteci uygulamanızda CLR tür adını belirterek döndüren kendi Fabrika de sağlayabilirsiniz @ServiceHost yönergesi.</span><span class="sxs-lookup"><span data-stu-id="c0a70-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="c0a70-124">Amaç temel durumlarda, uygulama kendi Fabrika anlaşılır alıştırma olması gerekliliğidir.</span><span class="sxs-lookup"><span data-stu-id="c0a70-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="c0a70-125">Örneğin, özel bir işte <xref:System.ServiceModel.Activation.ServiceHostFactory> türetilmiş döndüren <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="c0a70-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="c0a70-126">Bu fabrika varsayılan fabrika yerine kullanmak için tür adı sağlayın. @ServiceHost yönergesi aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="c0a70-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="c0a70-127">Varken teknik sınır yapmak istediğinizi <xref:System.ServiceModel.ServiceHost> gelen dönüş <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, Fabrika uygulamaları olabildiğince basit olarak tutmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c0a70-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="c0a70-128">Özel mantığı çok sayıda varsa, yeniden kullanılabilir olması için bu mantığı, konak yerine içinde Fabrika içinde koymak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="c0a70-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="c0a70-129">Burada bahsedilen barındırma API'si bir daha fazla katmana yoktur.</span><span class="sxs-lookup"><span data-stu-id="c0a70-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="c0a70-130">WCF de sahip <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, içinden <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türetilir.</span><span class="sxs-lookup"><span data-stu-id="c0a70-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="c0a70-131">Burada, meta veri sistemini büyük bölümlerini kendi özelleştirilmiş oluşturma ile takas gerekir daha Gelişmiş senaryolar için bu mevcut.</span><span class="sxs-lookup"><span data-stu-id="c0a70-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
