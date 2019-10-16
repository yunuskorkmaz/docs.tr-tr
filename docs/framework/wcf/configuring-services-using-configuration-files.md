---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 9a8db0670fff604cc9db8279ab1566e6e3fd3c8d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320684"
---
# <a name="configuring-services-using-configuration-files"></a>Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyası ile yapılandırmak, dağıtım noktasında, tasarım zamanında değil, uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar. Bu konu başlığı altında sunulan birincil teknikler özetlenmektedir.  
  
 WCF hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir. En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web. config dosyasına eklenir. Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir. Ayrıca, WCF, bir hizmet için en temel özellikleri hızlıca seçmenizi sağlayan, sistem tarafından sunulan çeşitli öğeleri içerir. @No__t-0 ' dan başlayarak WCF, WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir. Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı, hizmetinizi bazı standart uç noktalarla ve varsayılan bağlama/davranışla otomatik olarak yapılandırır. Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.  
  
 Daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md). En yaygın kullanılan öğelerin listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md). Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
> [!IMPORTANT]
> Bir hizmetin iki farklı sürümünün dağıtıldığı yan yana senaryolar dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmeniz gerekir. Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümleri arasında paylaşılmaları ve .NET Framework farklı sürümlerinde çalışıyor olması olabilir.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System. Configuration: Web. config ve App. config  
 WCF .NET Framework System. Configuration yapılandırma sistemini kullanır.  
  
 Bir hizmeti Visual Studio 'da yapılandırırken, ayarları belirtmek için bir Web. config dosyası ya da bir App. config dosyası kullanın. Yapılandırma dosyası adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir. Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web. config dosyası kullanın. Başka bir barındırma ortamı kullanıyorsanız, bir App. config dosyası kullanın.  
  
 Visual Studio 'da, son yapılandırma dosyasını oluşturmak için App. config adlı dosya kullanılır. Yapılandırma için gerçekten kullanılan son ad, derleme adına bağlıdır. Örneğin, "Cohowınara. exe" adlı bir derlemenin son yapılandırma dosyası adı "Cohowınara. exe. config" vardır. Ancak, yalnızca App. config dosyasını değiştirmeniz gerekir. Bu dosyada yapılan değişiklikler derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.  
  
 App. config dosyasını kullanarak, yapılandırma sistemi App. config dosyasını, uygulama başladığında ve yapılandırma uygulandığında Machine. config dosyasının içeriğiyle birleştirir. Bu mekanizma, Machine. config dosyasında makine genelindeki ayarların tanımlanmasını sağlar. Machine. config dosyasının ayarlarını geçersiz kılmak için App. config dosyası kullanılabilir; Ayrıca, Machine. config dosyasındaki ayarları, kullanıldıkları şekilde de kilitle. Web. config durumunda, yapılandırma sistemi tüm dizinlerde Web. config dosyalarını, uygulanan yapılandırma ile uygulama dizinine birleştirir. Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi için <xref:System.Configuration> ad alanındaki konulara bakın.  
  
## <a name="major-sections-of-the-configuration-file"></a>Yapılandırma dosyasının ana bölümleri  
 Yapılandırma dosyasındaki ana bölümler aşağıdaki öğeleri içerir.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> Bağlamalar ve davranışlar bölümleri isteğe bağlıdır ve yalnızca gerekli olduğunda dahil edilir.  
  
### <a name="the-services-element"></a>@No__t-0services > öğesi  
 @No__t-0 öğesi, uygulamanın barındırdığı tüm hizmetlere ilişkin belirtimleri içerir. @No__t-0 ' da Basitleştirilmiş yapılandırma modeliyle başlayarak bu bölüm isteğe bağlıdır.  
  
 [\<hizmetleri >](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>@No__t-0service > öğesi  
 Her hizmet şu özniteliklere sahiptir:  
  
- `name`. Hizmet sözleşmesinin bir uygulamasını sağlayan türü belirtir. Bu, ad alanı, nokta ve daha sonra tür adından oluşan tam nitelikli bir addır. Örneğin `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. @No__t-1 öğesinde bulunan `behavior` öğelerinden birinin adını belirtir. Belirtilen davranış, hizmetin kimliğe bürünmeye izin verip etmeyeceğini gibi eylemleri yönetir. Değeri boş bir addır veya `behaviorConfiguration` sağlanmamışsa, varsayılan hizmet davranışı kümesi hizmete eklenir.  
  
- [\< hizmet >](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>@No__t-0endpoint > öğesi  
 Her uç nokta, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve bir sözleşme gerektirir:  
  
- `address`. Hizmetin temel adresine göreli olarak verilen mutlak bir adres veya hizmet olan Tekdüzen Kaynak tanımlayıcısı 'nı (URI) belirtir. Boş bir dizeye ayarlanırsa, uç noktanın hizmet için <xref:System.ServiceModel.ServiceHost> oluşturulurken belirtilen temel adreste kullanılabilir olduğunu gösterir.  
  
- `binding`. Genellikle <xref:System.ServiceModel.WSHttpBinding> gibi sistem tarafından sağlanmış bir bağlamayı belirtir, ancak kullanıcı tanımlı bağlamayı da belirtebilir. Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, işlemlerin veya akışın desteklenip desteklenmediğini ya da etkin olup olmadığını belirler.  
  
- `bindingConfiguration`. Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu, `bindings` öğesinde uygun `binding` öğesi yapılandırılarak yapılabilir. Bu özniteliğe, varsayılan değerleri değiştirmek için kullanılan `binding` öğesinin `name` özniteliğiyle aynı değer verilmelidir. Hiçbir ad verilmezse veya bağlamada `bindingConfiguration` belirtilmemişse, son noktada bağlama türünün varsayılan bağlaması kullanılır.  
  
- `contract`. Sözleşmeyi tanımlayan arabirimi belirtir. Bu, `service` öğesinin `name` özniteliği tarafından belirtilen ortak dil çalışma zamanı (CLR) türünde uygulanan arabirimdir.  
  
- [\<uç nokta >](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>@No__t-0bindings > öğesi  
 @No__t-0 öğesi, herhangi bir hizmette tanımlı herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.  
  
 [\<bindings >](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>@No__t-0binding > öğesi  
 @No__t-1 öğesinde yer alan `binding` öğeleri, sistem tarafından belirtilen bağlamalardan biri olabilir ( [sistem tarafından belirtilen bağlamaları](system-provided-bindings.md)görebilir) veya özel bir bağlama (bkz. [Özel Bağlamalar](./extending/custom-bindings.md)). @No__t-0 öğesi, `endpoint` öğesinin `bindingConfiguration` özniteliğinde belirtilen uç nokta ile bağlamayı ilişkilendiren bir `name` özniteliğine sahiptir. Ad belirtilmemişse, o bağlama o bağlama türünün varsayılan değerine karşılık gelir.  
  
Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](configuring-services.md).
  
 [\< bağlama >](../misc/binding.md)  
  
### <a name="the-behaviors-element"></a>@No__t-0davranışlar > öğesi  
 Bu, bir hizmetin davranışlarını tanımlayan `behavior` öğelerinin kapsayıcı öğesidir.  
  
 [\<davranışlar >](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>@No__t-0behavior > öğesi  
 Her `behavior` öğesi bir `name` özniteliğiyle tanımlanır ve < `throttling` > veya özel bir davranış gibi sistem tarafından sağlanan bir davranış sağlar. Ad verilmezse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışına karşılık gelir.  
  
 [\<davranış >](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Bağlama ve davranış yapılandırmalarının kullanımı  
 WCF, yapılandırmada bir başvuru sistemi kullanarak uç noktalar arasında yapılandırmaların paylaşılmasını kolaylaştırır. Yapılandırma değerlerini bir uç noktaya doğrudan atamak yerine, bağlama ilgili yapılandırma değerleri `<binding>` bölümündeki `bindingConfiguration` öğelerinde gruplandırılır. Bağlama yapılandırması, bağlamada adlandırılmış bir ayar grubudur. Uç noktalar daha sonra ada göre `bindingConfiguration` ' a başvurabilir.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 @No__t-1 ' in `name` `<binding>` öğesinde ayarlanır. @No__t-0, bağlama türünün kapsamı içinde benzersiz bir dize olmalıdır — bu durumda, [< BasicHttpBinding @ no__t-2](../configure-apps/file-schema/wcf/basichttpbinding.md)veya varsayılan bağlamaya başvuracak boş bir değer. Uç nokta `bindingConfiguration` özniteliğini bu dizeye ayarlayarak yapılandırmaya bağlanır.  
  
 @No__t-0, aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 Varsayılan hizmet davranışı kümesinin hizmete eklendiğini unutmayın. Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaların paylaşmasına izin verir. Makine genelindeki kapsam gerekliyse, Machine. config içinde bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App. config dosyalarında kullanılabilir. [Yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md) , yapılandırmaların oluşturulmasını kolaylaştırır.  
  
## <a name="behavior-merge"></a>Davranış birleştirme  
 Davranış birleştirme özelliği, bir dizi ortak davranışın sürekli olarak kullanılmasını istediğinizde davranışları yönetmeyi kolaylaştırır. Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışlar belirtmenizi sağlar ve hizmetlerin, yapılandırma hiyerarşisinin birden fazla düzeyinden davranışları devralmasını sağlar. Bunun nasıl çalıştığını görmek için, IIS 'de aşağıdaki sanal dizin düzenine sahip olduğunu varsayın:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 @No__t-0 dosyanız aşağıdaki içeriğe sahiptir:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Ve şu içeriklerle ~ \Child\Web.config konumunda bulunan bir alt Web. config dosyası vardır:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 ~ \Child\service.exe konumunda bulunan hizmet, hem serviceDebug hem de serviceMetadata davranışlarına sahip olsa da çalışır. ~ \Service.exe yolunda bulunan hizmette yalnızca serviceDebug davranışı olur. Ne olacağı, aynı ada sahip iki davranış koleksiyonunun (Bu durumda boş dize) birleştirilmesidir.  
  
 Ayrıca, \<clear > etiketini kullanarak davranış koleksiyonlarını temizleyebilir ve \<remove > etiketini kullanarak koleksiyonlardan ayrı davranışları kaldırmış olabilirsiniz. Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca serviceMetadata davranışına sahip olmasına neden olur:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Davranış birleştirme yukarıda ve adlandırılmış davranış koleksiyonları da gösterildiği gibi adsız davranış koleksiyonları için yapılır.  
  
 Davranış birleştirme, Web. config dosyalarının kök Web. config dosyası ve Machine. config ile hiyerarşik olarak birleştirileyeceği IIS barındırma ortamında çalışmaktadır. Ancak bu, Machine. config 'in App. config dosyasıyla birleştirilebileceği uygulama ortamında da kullanılır.  
  
 Davranış birleştirme, yapılandırma içindeki uç nokta davranışları ve hizmet davranışları için geçerlidir.  
  
 Bir alt davranış koleksiyonu, üst davranış koleksiyonunda zaten bulunan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar. Bu nedenle, bir üst davranış koleksiyonu `<serviceMetadata httpGetEnabled="False" />` ve bir alt davranış koleksiyonu `<serviceMetadata httpGetEnabled="True" />` ise, alt davranış davranış koleksiyonundaki üst davranışı geçersiz kılar ve httpGetEnabled "true" olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](simplified-configuration.md)
- [WCF hizmetlerini yapılandırma](configuring-services.md)
- [\< hizmet >](../configure-apps/file-schema/wcf/service.md)
- [\< bağlama >](../misc/binding.md)
