---
title: ServiceHostFactory Kullanarak Barındırmayı Genişletme
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: d2224ea683326679efdad368cf2ff7b2b95f4dba
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273132"
---
# <a name="extending-hosting-using-servicehostfactory"></a>ServiceHostFactory Kullanarak Barındırmayı Genişletme

<xref:System.ServiceModel.ServiceHost>Windows Communication Foundation (WCF) içindeki barındırma hizmetleri için Standart API, WCF mimarisinde bir genişletilebilirlik noktasıdır. Kullanıcılar <xref:System.ServiceModel.ServiceHost> , <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> <xref:System.ServiceModel.Description.ServiceDescription> hizmeti açmadan önce varsayılan uç noktaları imperatively veya değiştirme davranışlarına eklemek için kullanmak üzere geçersiz kılmak üzere ' dan kendi ana bilgisayar sınıflarını türetilebilir.  
  
 Self-Host ortamında, <xref:System.ServiceModel.ServiceHost> Konağı örnekleyen kodu yazdığınız ve sonra <xref:System.ServiceModel.ICommunicationObject.Open> onu başlattıktan sonra bu kodu çağıran için özel bir oluşturmanız gerekmez. Bu iki adım arasında istediğiniz her şeyi yapabilirsiniz. Örneğin, yeni bir ekleyebilirsiniz <xref:System.ServiceModel.Description.IServiceBehavior> :  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Bu yaklaşım yeniden kullanılabilir değil. Açıklamayı işleyen kod ana bilgisayar programına (Bu durumda Main () işlevi) kodlanır, bu nedenle bu mantığı diğer bağlamlarda yeniden kullanmak zordur. Ayrıca, gerekli kodu gerektirmeyen başka bir ekleme yöntemi de vardır <xref:System.ServiceModel.Description.IServiceBehavior> . İçinden bir özniteliği türetebilir <xref:System.ServiceModel.ServiceBehaviorAttribute> ve hizmet uygulama türüne koyabilirsiniz veya özel bir davranışı yapılandırılabilir hale getirebilirsiniz ve yapılandırma kullanarak dinamik olarak oluşturabilirsiniz.  
  
 Ancak, bu sorunu çözmek için örneğin küçük bir çeşitlemesi de kullanılabilir. Tek bir yaklaşım, `Main()` ' ın ve ' nin <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> özel bir türevi olan yöntemine ekleyen kodu taşımadır <xref:System.ServiceModel.ServiceHost> :  
  
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
  
 Ardından, içinde şunları `Main()` kullanabilirsiniz:  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Artık özel mantığı birçok farklı konak yürütülebilir dosyalarında kolayca yeniden kullanılabilecek temiz bir soyutlamakta kapsülledik.  
  
 Bu özel, <xref:System.ServiceModel.ServiceHost> Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti 'nin (was) içinden bu özel kullanım için hemen açık değildir. Barındırma ortamı, uygulamanın adına bir örneklenme yaptığından, bu ortamlar Self-Host ortamından farklıdır <xref:System.ServiceModel.ServiceHost> . IIS ve barındırma altyapısı, özel türev ile ilgili herhangi bir şeyi bilmez <xref:System.ServiceModel.ServiceHost> .  
  
 , <xref:System.ServiceModel.Activation.ServiceHostFactory> IIS veya was içinden özel erişim sorununu çözmek için tasarlandı <xref:System.ServiceModel.ServiceHost> . Öğesinden türetilen özel bir ana bilgisayar <xref:System.ServiceModel.ServiceHost> dinamik olarak yapılandırıldığı ve potansiyel olarak çeşitli türlerde olduğu için, barındırma ortamı hiçbir şekilde doğrudan bir örneği oluşturur. Bunun yerine, WCF, barındırma ortamı ve hizmetin somut türü arasında bir yöneltme katmanı sağlamak için bir fabrika kalıbı kullanır. Aksi belirtilmedikçe, bir örneği döndüren varsayılan bir uygulamasını kullanır <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.ServiceHost> . Ancak, yönergede fabrika uygulamanızın CLR türü adını belirterek türetilmiş ana bilgisayarınızı döndüren kendi fabrikanızı da sağlayabilirsiniz @ServiceHost .  
  
 Amaç, temel durumlarda kendi fabrikanızın uygulanması, sorunsuz bir alıştırma olmalıdır. Örneğin, <xref:System.ServiceModel.Activation.ServiceHostFactory> bir türeme döndüren özel bir özel <xref:System.ServiceModel.ServiceHost> :  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Varsayılan fabrika yerine bu fabrikası kullanmak için, yönergede tür adını @ServiceHost aşağıdaki gibi sağlayın:  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <xref:System.ServiceModel.ServiceHost>' Den geri dönmenizi istediğiniz teknik sınır olmasa <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A> da, fabrika uygulamalarınızı mümkün olduğunca basit tutmanız önerilir. Çok sayıda özel mantığınızın olması durumunda, yeniden kullanılabilir olması için bu mantığı fabrika yerine konağın içine koymak daha iyidir.  
  
 Barındırma API 'sinde burada bahsedilen bir katman daha vardır. WCF Ayrıca <xref:System.ServiceModel.ServiceHostBase> , ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türeten ve. Bunlar, meta veri sisteminin büyük kısımlarını kendi özelleştirilmiş oluşturma işlemleri ile takas etmeniz gereken daha gelişmiş senaryolar için mevcuttur.
