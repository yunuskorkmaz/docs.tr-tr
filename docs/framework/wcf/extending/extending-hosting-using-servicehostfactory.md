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
# <a name="extending-hosting-using-servicehostfactory"></a>ServiceHostFactory Kullanarak Barındırmayı Genişletme
Windows Communication Foundation ( <xref:System.ServiceModel.ServiceHost> WCF) içindeki barındırma hizmetleri için Standart API, WCF mimarisinde bir genişletilebilirlik noktasıdır. Kullanıcılar, hizmeti açmadan önce varsayılan uç noktaları <xref:System.ServiceModel.ServiceHost>imperatively veya değiştirme davranışlarına <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> eklemek için <xref:System.ServiceModel.Description.ServiceDescription> kullanmak üzere geçersiz kılmak üzere ' dan kendi ana bilgisayar sınıflarını türetilebilir.  
  
 Self-Host ortamında, Konağı örnekleyen kodu yazdığınız ve sonra onu başlattıktan sonra <xref:System.ServiceModel.ServiceHost> bu kodu çağıran <xref:System.ServiceModel.ICommunicationObject.Open> için özel bir oluşturmanız gerekmez. Bu iki adım arasında istediğiniz her şeyi yapabilirsiniz. Örneğin, yeni <xref:System.ServiceModel.Description.IServiceBehavior>bir ekleyebilirsiniz:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Bu yaklaşım yeniden kullanılabilir değil. Açıklamayı işleyen kod ana bilgisayar programına (Bu durumda Main () işlevi) kodlanır, bu nedenle bu mantığı diğer bağlamlarda yeniden kullanmak zordur. Ayrıca, gerekli kodu gerektirmeyen başka bir <xref:System.ServiceModel.Description.IServiceBehavior> ekleme yöntemi de vardır. İçinden <xref:System.ServiceModel.ServiceBehaviorAttribute> bir özniteliği türetebilir ve hizmet uygulama türüne koyabilirsiniz veya özel bir davranışı yapılandırılabilir hale getirebilirsiniz ve yapılandırma kullanarak dinamik olarak oluşturabilirsiniz.  
  
 Ancak, bu sorunu çözmek için örneğin küçük bir çeşitlemesi de kullanılabilir. Tek bir yaklaşım, ' ın `Main()` ve ' <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> nin özel bir türevi <xref:System.ServiceModel.ServiceHost>olan yöntemine ekleyen kodu taşımadır:  
  
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
  
 Ardından, içinde `Main()` şunları kullanabilirsiniz:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Artık özel mantığı birçok farklı konak yürütülebilir dosyalarında kolayca yeniden kullanılabilecek temiz bir soyutlamakta kapsülledik.  
  
 Bu özel, Internet Information Services (IIS) veya Windows işlem <xref:System.ServiceModel.ServiceHost> etkinleştirme hizmeti 'nin (was) içinden bu özel kullanım için hemen açık değildir. Barındırma ortamı, uygulamanın adına bir örneklenme <xref:System.ServiceModel.ServiceHost> yaptığından, bu ortamlar Self-Host ortamından farklıdır. IIS ve barındırma altyapısı, özel <xref:System.ServiceModel.ServiceHost> türev ile ilgili herhangi bir şeyi bilmez.  
  
 , <xref:System.ServiceModel.Activation.ServiceHostFactory> IIS veya was içinden özel <xref:System.ServiceModel.ServiceHost> erişim sorununu çözmek için tasarlandı. Öğesinden <xref:System.ServiceModel.ServiceHost> türetilen özel bir ana bilgisayar dinamik olarak yapılandırıldığı ve potansiyel olarak çeşitli türlerde olduğu için, barındırma ortamı hiçbir şekilde doğrudan bir örneği oluşturur. Bunun yerine, WCF, barındırma ortamı ve hizmetin somut türü arasında bir yöneltme katmanı sağlamak için bir fabrika kalıbı kullanır. Aksi belirtilmedikçe, bir <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.ServiceHost>örneği döndüren varsayılan bir uygulamasını kullanır. Ancak, @ServiceHost yönergede fabrika uygulamanızın clr türü adını belirterek türetilmiş ana bilgisayarınızı döndüren kendi fabrikanızı da sağlayabilirsiniz.  
  
 Amaç, temel durumlarda kendi fabrikanızın uygulanması, sorunsuz bir alıştırma olmalıdır. Örneğin, bir türeme <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.ServiceHost>döndüren özel bir özel:  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Varsayılan fabrika yerine bu fabrikası kullanmak için, @ServiceHost yönergede tür adını aşağıdaki gibi sağlayın:  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 ' Den <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>geri dönmenizi istediğiniz teknik sınır olmasa da, fabrika uygulamalarınızı mümkün olduğunca basit tutmanız önerilir. Çok sayıda özel mantığınızın olması durumunda, yeniden kullanılabilir olması için bu mantığı fabrika yerine konağın içine koymak daha iyidir.  
  
 Barındırma API 'sinde burada bahsedilen bir katman daha vardır. WCF Ayrıca <xref:System.ServiceModel.ServiceHostBase> , ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türeten <xref:System.ServiceModel.ServiceHost> ve. Bunlar, meta veri sisteminin büyük kısımlarını kendi özelleştirilmiş oluşturma işlemleri ile takas etmeniz gereken daha gelişmiş senaryolar için mevcuttur.
