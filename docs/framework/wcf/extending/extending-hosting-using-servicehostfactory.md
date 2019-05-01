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
# <a name="extending-hosting-using-servicehostfactory"></a>ServiceHostFactory Kullanarak Barındırmayı Genişletme
Standart <xref:System.ServiceModel.ServiceHost> Windows Communication Foundation (WCF) hizmetlerini barındırma API'si, WCF mimarisinin bir genişletilebilirlik noktası. Kullanıcılar, kendi ana bilgisayar sınıflarından türetilebilir <xref:System.ServiceModel.ServiceHost>, genellikle geçersiz kılmak için <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> kullanılacak <xref:System.ServiceModel.Description.ServiceDescription> kesin varsayılan uç noktalarını eklemek veya hizmet açmadan önce davranışları değiştirmek için.  
  
 Barındırma ortamında bir özel Oluştur gerekmez <xref:System.ServiceModel.ServiceHost> konak başlatan kodu yazın ve ardından çağırmak için <xref:System.ServiceModel.ICommunicationObject.Open> sonra bu örneği üzerinde. Bu iki adımı arasında istediğiniz yapabilirsiniz. Örneğin, yeni bir ekleme olabilir <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Bu yaklaşım, yeniden kullanılabilir değil. Açıklama işleyen kod, ana bilgisayar kodlanmış program (Bu durumda, Main() işlevi), diğer bağlamlarda bu mantığı yeniden zor olur. Eklemenin başka yolları da vardır bir <xref:System.ServiceModel.Description.IServiceBehavior> kesinlik temelli kod gerektirmez. Bir öznitelik alma türetebilirsiniz <xref:System.ServiceModel.ServiceBehaviorAttribute> ve hizmet uygulamanızı türü veya özel bir davranış yapılandırılabilir hale getirebilir ve onu yapılandırma kullanılarak dinamik olarak oluşturmak, yerleştirin.  
  
 Bununla birlikte, küçük bir değişim Örneğin bu sorunu çözmek için de kullanılabilir. Bir yaklaşım ise tanesi ServiceBehavior ekler kodu taşımak için `Main()` ve <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> yöntemi bir özel türevi <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Ardından, içinde `Main()` kullanabilirsiniz:  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Artık birçok farklı bir konak yürütülebilir dosyalar arasında kolayca yeniden kullanılabilir bir temiz soyutlama uygulamasına özel mantığı kapsüllenmiş.  
  
 Bu özel kullanmaya nasıl hemen açık değilse <xref:System.ServiceModel.ServiceHost> gelen Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) içinde. Barındırma ortamı bir örnekleme olduğundan bu ortamlarda barındırma ortamı farklı <xref:System.ServiceModel.ServiceHost> uygulama adına. IIS ve WAS'ta barındırma altyapısını kendi özel hakkında hiçbir şey bilmez <xref:System.ServiceModel.ServiceHost> Türev.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> Özel erişim bu sorunu çözmek için tasarlanmış <xref:System.ServiceModel.ServiceHost> dan IIS ya da WAS içinde. Özel bir konak olmadığından türetilir <xref:System.ServiceModel.ServiceHost> dinamik olarak yapılandırılır ve potansiyel olarak çeşitli türleri, barındırma ortamı hiçbir zaman doğrudan örneğini oluşturduğunda. Bunun yerine, WCF, barındırma ortamı ve hizmetin somut türü arasında bir yöneltme katman sağlamak için bir Fabrika deseni kullanır. Aksi takdirde söyleyin sürece, varsayılan bir uygulama kullanır. <xref:System.ServiceModel.Activation.ServiceHostFactory> örneğini döndüren <xref:System.ServiceModel.ServiceHost>. Ancak türetilmiş ana bilgisayar üreteci uygulamanızda CLR tür adını belirterek döndüren kendi Fabrika de sağlayabilirsiniz @ServiceHost yönergesi.  
  
 Amaç temel durumlarda, uygulama kendi Fabrika anlaşılır alıştırma olması gerekliliğidir. Örneğin, özel bir işte <xref:System.ServiceModel.Activation.ServiceHostFactory> türetilmiş döndüren <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Bu fabrika varsayılan fabrika yerine kullanmak için tür adı sağlayın. @ServiceHost yönergesi aşağıdaki gibi:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Varken teknik sınır yapmak istediğinizi <xref:System.ServiceModel.ServiceHost> gelen dönüş <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, Fabrika uygulamaları olabildiğince basit olarak tutmanızı öneririz. Özel mantığı çok sayıda varsa, yeniden kullanılabilir olması için bu mantığı, konak yerine içinde Fabrika içinde koymak daha iyidir.  
  
 Burada bahsedilen barındırma API'si bir daha fazla katmana yoktur. WCF de sahip <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, içinden <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türetilir. Burada, meta veri sistemini büyük bölümlerini kendi özelleştirilmiş oluşturma ile takas gerekir daha Gelişmiş senaryolar için bu mevcut.
