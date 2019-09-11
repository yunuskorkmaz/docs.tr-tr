---
title: ServiceHostFactory Kullanarak Barındırmayı Genişletme
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: de6a590b94285872dd77006eda7f86d5d629be9d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849907"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="d8860-102">ServiceHostFactory Kullanarak Barındırmayı Genişletme</span><span class="sxs-lookup"><span data-stu-id="d8860-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="d8860-103">Windows Communication Foundation ( <xref:System.ServiceModel.ServiceHost> WCF) içindeki barındırma hizmetleri için Standart API, WCF mimarisinde bir genişletilebilirlik noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="d8860-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="d8860-104">Kullanıcılar, hizmeti açmadan önce varsayılan uç noktaları <xref:System.ServiceModel.ServiceHost>imperatively veya değiştirme davranışlarına <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> eklemek için <xref:System.ServiceModel.Description.ServiceDescription> kullanmak üzere geçersiz kılmak üzere ' dan kendi ana bilgisayar sınıflarını türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="d8860-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="d8860-105">Self-Host ortamında, Konağı örnekleyen kodu yazdığınız ve sonra onu başlattıktan sonra <xref:System.ServiceModel.ServiceHost> bu kodu çağıran <xref:System.ServiceModel.ICommunicationObject.Open> için özel bir oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d8860-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="d8860-106">Bu iki adım arasında istediğiniz her şeyi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8860-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="d8860-107">Örneğin, yeni <xref:System.ServiceModel.Description.IServiceBehavior>bir ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8860-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="d8860-108">Bu yaklaşım yeniden kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="d8860-108">This approach is not reusable.</span></span> <span data-ttu-id="d8860-109">Açıklamayı işleyen kod ana bilgisayar programına (Bu durumda Main () işlevi) kodlanır, bu nedenle bu mantığı diğer bağlamlarda yeniden kullanmak zordur.</span><span class="sxs-lookup"><span data-stu-id="d8860-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="d8860-110">Ayrıca, gerekli kodu gerektirmeyen başka bir <xref:System.ServiceModel.Description.IServiceBehavior> ekleme yöntemi de vardır.</span><span class="sxs-lookup"><span data-stu-id="d8860-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="d8860-111">İçinden <xref:System.ServiceModel.ServiceBehaviorAttribute> bir özniteliği türetebilir ve hizmet uygulama türüne koyabilirsiniz veya özel bir davranışı yapılandırılabilir hale getirebilirsiniz ve yapılandırma kullanarak dinamik olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8860-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="d8860-112">Ancak, bu sorunu çözmek için örneğin küçük bir çeşitlemesi de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8860-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="d8860-113">Tek bir yaklaşım, ' ın `Main()` ve ' <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> nin özel bir türevi <xref:System.ServiceModel.ServiceHost>olan yöntemine ekleyen kodu taşımadır:</span><span class="sxs-lookup"><span data-stu-id="d8860-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
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
  
 <span data-ttu-id="d8860-114">Ardından, içinde `Main()` şunları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8860-114">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="d8860-115">Artık özel mantığı birçok farklı konak yürütülebilir dosyalarında kolayca yeniden kullanılabilecek temiz bir soyutlamakta kapsülledik.</span><span class="sxs-lookup"><span data-stu-id="d8860-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="d8860-116">Bu özel, Internet Information Services (IIS) veya Windows işlem <xref:System.ServiceModel.ServiceHost> etkinleştirme hizmeti 'nin (was) içinden bu özel kullanım için hemen açık değildir.</span><span class="sxs-lookup"><span data-stu-id="d8860-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="d8860-117">Barındırma ortamı, uygulamanın adına bir örneklenme <xref:System.ServiceModel.ServiceHost> yaptığından, bu ortamlar Self-Host ortamından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d8860-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="d8860-118">IIS ve barındırma altyapısı, özel <xref:System.ServiceModel.ServiceHost> türev ile ilgili herhangi bir şeyi bilmez.</span><span class="sxs-lookup"><span data-stu-id="d8860-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="d8860-119">, <xref:System.ServiceModel.Activation.ServiceHostFactory> IIS veya was içinden özel <xref:System.ServiceModel.ServiceHost> erişim sorununu çözmek için tasarlandı.</span><span class="sxs-lookup"><span data-stu-id="d8860-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="d8860-120">Öğesinden <xref:System.ServiceModel.ServiceHost> türetilen özel bir ana bilgisayar dinamik olarak yapılandırıldığı ve potansiyel olarak çeşitli türlerde olduğu için, barındırma ortamı hiçbir şekilde doğrudan bir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d8860-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="d8860-121">Bunun yerine, WCF, barındırma ortamı ve hizmetin somut türü arasında bir yöneltme katmanı sağlamak için bir fabrika kalıbı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8860-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="d8860-122">Aksi belirtilmedikçe, bir <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.ServiceHost>örneği döndüren varsayılan bir uygulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8860-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d8860-123">Ancak, @ServiceHost yönergede fabrika uygulamanızın clr türü adını belirterek türetilmiş ana bilgisayarınızı döndüren kendi fabrikanızı da sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8860-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="d8860-124">Amaç, temel durumlarda kendi fabrikanızın uygulanması, sorunsuz bir alıştırma olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d8860-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="d8860-125">Örneğin, bir türeme <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.ServiceHost>döndüren özel bir özel:</span><span class="sxs-lookup"><span data-stu-id="d8860-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="d8860-126">Varsayılan fabrika yerine bu fabrikası kullanmak için, @ServiceHost yönergede tür adını aşağıdaki gibi sağlayın:</span><span class="sxs-lookup"><span data-stu-id="d8860-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="d8860-127">' Den <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>geri dönmenizi istediğiniz teknik sınır olmasa da, fabrika uygulamalarınızı mümkün olduğunca basit tutmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="d8860-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="d8860-128">Çok sayıda özel mantığınızın olması durumunda, yeniden kullanılabilir olması için bu mantığı fabrika yerine konağın içine koymak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="d8860-128">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="d8860-129">Barındırma API 'sinde burada bahsedilen bir katman daha vardır.</span><span class="sxs-lookup"><span data-stu-id="d8860-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="d8860-130">WCF Ayrıca <xref:System.ServiceModel.ServiceHostBase> , ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türeten <xref:System.ServiceModel.ServiceHost> ve.</span><span class="sxs-lookup"><span data-stu-id="d8860-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="d8860-131">Bunlar, meta veri sisteminin büyük kısımlarını kendi özelleştirilmiş oluşturma işlemleri ile takas etmeniz gereken daha gelişmiş senaryolar için mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d8860-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
