---
title: ServiceHostFactory Kullanarak Barındırmayı Genişletme
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="extending-hosting-using-servicehostfactory"></a>ServiceHostFactory Kullanarak Barındırmayı Genişletme
Standart <xref:System.ServiceModel.ServiceHost> Windows Communication Foundation (WCF) hizmetlerini barındıran için API WCF mimarisinde bir genişletilebilirlik noktasıdır. Kullanıcılar kendi ana bilgisayar sınıftan türetilen <xref:System.ServiceModel.ServiceHost>, genellikle geçersiz kılmak için <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> kullanmak için <xref:System.ServiceModel.Description.ServiceDescription> imperatively varsayılan uç noktaları eklemek veya hizmet açmadan önce davranışları değiştirmek için.  
  
 Kendini barındırma ortamında bir özel Oluştur gerekmez <xref:System.ServiceModel.ServiceHost> ana bilgisayarı başlatır kodu yazın ve ardından çağırın çünkü <xref:System.ServiceModel.ICommunicationObject.Open> Bu örneği sonra üzerinde. Bu iki adımları arasında istediğiniz yapabilirsiniz. Örneğin, yeni bir ekleyebilirsiniz <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Bu yaklaşım yeniden kullanılabilir değil. Açıklama işleyen kodu ana bilgisayar kodlanmış program (Bu durumda, Main() işlevi), bu mantığı diğer bağlamlarda yeniden zordur. Ekleme başka yolları da vardır bir <xref:System.ServiceModel.Description.IServiceBehavior> kesinlik temelli kod gerektirmez. Özniteliği türetilemeyeceğini <xref:System.ServiceModel.ServiceBehaviorAttribute> ve hizmet uygulamanızı türü veya özel bir davranış yapılandırılabilir hale getirebilir ve dinamik olarak yapılandırma kullanarak oluşturan olduğunu yerleştirin.  
  
 Ancak, küçük bir çeşididir Örneğin bu sorunu çözmek için de kullanılabilir. Bir yaklaşım ise kullanıma ServiceBehavior ekleyen kod taşımak için `Main()` ve içine <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> özel bir türevi yöntemi <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Şimdi birçok farklı ana bilgisayar yürütülebilir dosyalar arasında kolayca yeniden kullanılabilir bir temiz soyutlama içine özel mantık kapsüllenmiş.  
  
 Bu özel kullanmayı hemen göze erişilebilir <xref:System.ServiceModel.ServiceHost> gelen Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) içinde. Barındırma ortamı bir örneği olduğundan bu ortamlarda kendini barındırma ortamı farklı <xref:System.ServiceModel.ServiceHost> uygulama adına. IIS ve WAS'ta barındırma altyapı özel hakkında hiçbir şey bilmez <xref:System.ServiceModel.ServiceHost> türevi.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> Özel erişme bu sorunu çözmek için tasarlanmıştır <xref:System.ServiceModel.ServiceHost> gelen IIS ya da WAS içinde. Özel bir ana bilgisayar olduğundan türetilmiş <xref:System.ServiceModel.ServiceHost> dinamik olarak yapılandırılır ve potansiyel olarak çeşitli türlerde barındırma ortamı hiçbir zaman onu doğrudan başlatır. Bunun yerine, WCF yöneltme barındırma ortamı ve hizmetin somut türü arasında katmanı sağlamak için Fabrika desen kullanır. Aksi takdirde söyleyin sürece, bir varsayılan uygulaması kullanır <xref:System.ServiceModel.Activation.ServiceHostFactory> örneği döndürür <xref:System.ServiceModel.ServiceHost>. Ancak Fabrika uygulamanızda CLR türü adını belirterek türetilmiş ana bilgisayarınız döndürür kendi Fabrika de sağlayabilirsiniz @ServiceHost yönergesi.  
  
 Amaç, temel durumlarda, kendi Fabrika uygulama düz iletme alıştırma olması gerektiğini ' dir. Örneğin, özel bir işte <xref:System.ServiceModel.Activation.ServiceHostFactory> türetilmiş döndüren <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Bu fabrikada yerine varsayılan fabrika kullanmak için tür adı sağlayın @ServiceHost şekilde yönergesi:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Varken teknik sınır için istediğiniz yapmayı <xref:System.ServiceModel.ServiceHost> döndürmek, <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, Fabrika uygulamaları olabildiğince basit tutmak öneririz. Çok sayıda özel mantık varsa, yeniden kullanılabilir olması için bu mantığı, ana bilgisayar yerine içinde Fabrika yerleştirilecek daha iyidir.  
  
 Burada belirtilen barındırma API bir daha fazla katmana yoktur. WCF de sahip <xref:System.ServiceModel.ServiceHostBase> ve <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, içinden <xref:System.ServiceModel.ServiceHost> ve <xref:System.ServiceModel.Activation.ServiceHostFactory> sırasıyla türetilir. Bu, kendi özelleştirilmiş oluşturmaları ile meta veri sistem büyük bölümlerini burada takas gerekir daha Gelişmiş senaryolar için mevcut.
