---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
description: WCF hizmeti için bir yapılandırma dosyasının Dağıtım sırasında Endpoint ve hizmet davranışı verileri sağlama esnekliğini nasıl sağladığını öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 1a3266ad8890436c9be9d0f2b231aeaca0f9236e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245433"
---
# <a name="configuring-services-using-configuration-files"></a>Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyası ile yapılandırmak, dağıtım noktasında, tasarım zamanında değil, uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar. Bu konu başlığı altında sunulan birincil teknikler özetlenmektedir.  
  
 WCF hizmeti, .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir. En yaygın olarak, XML öğeleri bir WCF hizmetini barındıran bir Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir. Öğeler, bir makine temelinde, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları değiştirmenize izin verir. Ayrıca, WCF, bir hizmet için en temel özellikleri hızlıca seçmenizi sağlayan, sistem tarafından sunulan çeşitli öğeleri içerir. WCF, .NET Framework 4 ' te başlayarak WCF yapılandırma gereksinimlerini kolaylaştıran yeni bir varsayılan yapılandırma modeliyle gelir. Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma zamanı, hizmetinizi bazı standart uç noktalarla ve varsayılan bağlama/davranışla otomatik olarak yapılandırır. Uygulamada, yapılandırma yazma, WCF uygulamalarının Programlamanın önemli bir parçasıdır.  
  
 Daha fazla bilgi için bkz. [Hizmetler Için bağlamaları yapılandırma](configuring-bindings-for-wcf-services.md). En yaygın kullanılan öğelerin listesi için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md). Varsayılan uç noktalar, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [WCF Hizmetleri Için](./samples/simplified-configuration-for-wcf-services.md) [Basitleştirilmiş yapılandırma](simplified-configuration.md) ve Basitleştirilmiş yapılandırma.  
  
> [!IMPORTANT]
> Bir hizmetin iki farklı sürümünün dağıtıldığı yan yana senaryolar dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmeniz gerekir. Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümleri arasında paylaşılmaları ve .NET Framework farklı sürümlerinde çalışıyor olması olabilir.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configurlama: Web.config ve App.config  
 WCF, .NET Framework System.Configuration yapılandırma sistemini kullanır.  
  
 Bir hizmeti Visual Studio 'da yapılandırırken, ayarları belirtmek için bir Web.config dosyası ya da bir App.config dosyası kullanın. Yapılandırma dosyası adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir. Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web.config dosyası kullanın. Başka bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.  
  
 Visual Studio 'da App.config adlı dosya, son yapılandırma dosyasını oluşturmak için kullanılır. Yapılandırma için gerçekten kullanılan son ad, derleme adına bağlıdır. Örneğin, "Cohowinery.exe" adlı bir derlemenin son yapılandırma dosyası adı "Cohowinery.exe.config" vardır. Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir. Bu dosyada yapılan değişiklikler derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.  
  
 App.config kullanarak, yapılandırma sistemi, uygulama başladığında ve yapılandırma uygulandığında App.config dosyasını Machine.config dosyanın içeriğiyle birleştirir. Bu mekanizma, Machine.config dosyasında makine genelindeki ayarların tanımlanmasını sağlar. App.config dosyası, Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; Ayrıca, Machine.config dosyadaki ayarları, bunların kullanılması için de kilitle. Web.config durumda, yapılandırma sistemi tüm dizinlerde bulunan Web.config dosyalarını, uygulanan yapılandırmayla uygulama dizinine en başta birleştirir. Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi için bkz. ad alanındaki konular <xref:System.Configuration> .  
  
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
  
### <a name="the-services-element"></a>\<services>Öğe  
 `services`Öğesi, uygulamanın barındırdığı tüm hizmetlere ilişkin belirtimleri içerir. .NET Framework 4 ' te Basitleştirilmiş yapılandırma modeliyle başlayarak bu bölüm isteğe bağlıdır.  
  
 [\<services>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<service>Öğe  
 Her hizmet şu özniteliklere sahiptir:  
  
- `name`. Hizmet sözleşmesinin bir uygulamasını sağlayan türü belirtir. Bu, ad alanı, nokta ve daha sonra tür adından oluşan tam nitelikli bir addır. Örneğin, `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. `behavior`Öğesinde bulunan öğelerden birinin adını belirtir `behaviors` . Belirtilen davranış, hizmetin kimliğe bürünmeye izin verip etmeyeceğini gibi eylemleri yönetir. Değeri boş bir ad ise veya Hayır sağlanmazsa, `behaviorConfiguration` varsayılan hizmet davranışı kümesi hizmete eklenir.  
  
- [\<service>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<endpoint>Öğe  
 Her uç nokta, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve bir sözleşme gerektirir:  
  
- `address`. Hizmetin temel adresine göreli olarak verilen mutlak bir adres veya hizmet olan Tekdüzen Kaynak tanımlayıcısı 'nı (URI) belirtir. Boş bir dizeye ayarlanırsa, uç noktanın hizmet için oluşturulurken belirtilen temel adreste kullanılabilir olduğunu gösterir <xref:System.ServiceModel.ServiceHost> .  
  
- `binding`. Genellikle gibi sistem tarafından sağlanmış bir bağlamayı belirtir <xref:System.ServiceModel.WSHttpBinding> , ancak kullanıcı tanımlı bağlamayı da belirtebilir. Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, işlemlerin veya akışın desteklenip desteklenmediğini ya da etkin olup olmadığını belirler.  
  
- `bindingConfiguration`. Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu, öğesinde uygun öğe yapılandırılarak yapılabilir `binding` `bindings` . Bu özniteliğe, `name` `binding` varsayılan değerleri değiştirmek için kullanılan öğesinin özniteliğiyle aynı değer verilmelidir. Hiçbir ad verilmezse veya bağlamada hiçbir değer `bindingConfiguration` belirtilmemişse, bağlantı türü için varsayılan bağlama uç noktada kullanılır.  
  
- `contract`. Sözleşmeyi tanımlayan arabirimi belirtir. Bu, öğesinin özniteliği tarafından belirtilen ortak dil çalışma zamanı (CLR) türünde uygulanan arabirimdir `name` `service` .  
  
- [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>\<bindings>Öğe  
 `bindings`Öğesi, herhangi bir hizmette tanımlı herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.  
  
 [\<bindings>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<binding>Öğe  
 `binding`Öğesinde yer alan öğeler, `bindings` sistem tarafından belirtilen bağlamalardan biri olabilir ( [sistem tarafından belirtilen bağlamaları](system-provided-bindings.md)görebilir) veya özel bir bağlama (bkz. [Özel Bağlamalar](./extending/custom-bindings.md)). `binding`Öğesi, `name` bağlamayı öğenin özniteliğinde belirtilen uç noktayla ilişkilendiren bir özniteliğe sahiptir `bindingConfiguration` `endpoint` . Ad belirtilmemişse, o bağlama o bağlama türünün varsayılan değerine karşılık gelir.  
  
Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [WCF hizmetlerini yapılandırma](configuring-services.md).
  
 [\<binding>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>\<behaviors>Öğe  
 Bu, `behavior` bir hizmetin davranışlarını tanımlayan öğeler için bir kapsayıcı öğesidir.  
  
 [\<behaviors>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<behavior>Öğe  
 Her `behavior` öğe bir öznitelik tarafından tanımlanır `name` ve <`throttling`> ya da özel bir davranış gibi sistem tarafından sağlanan bir davranış sağlar. Ad verilmezse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışına karşılık gelir.  
  
 [\<behavior>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Bağlama ve davranış yapılandırmalarının kullanımı  
 WCF, yapılandırmada bir başvuru sistemi kullanarak uç noktalar arasında yapılandırmaların paylaşılmasını kolaylaştırır. Yapılandırma değerlerini bir uç noktaya doğrudan atamak yerine, bağlama ilgili yapılandırma değerleri, `bindingConfiguration` bölümündeki öğelerde gruplandırılır `<binding>` . Bağlama yapılandırması, bağlamada adlandırılmış bir ayar grubudur. Uç noktalar daha sonra `bindingConfiguration` adına göre başvuru yapabilir.  
  
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
  
 `name` `bindingConfiguration` `<binding>` Öğesi öğesinde ayarlanır. `name`Bağlama türünün kapsamı içinde benzersiz bir dize olmalıdır — bu durumda [<\> BasicHttpBinding](../configure-apps/file-schema/wcf/basichttpbinding.md)veya varsayılan bağlamaya başvuracak boş bir değer. Uç nokta, özniteliğini bu dizeye ayarlayarak yapılandırmaya bağlanır `bindingConfiguration` .  
  
 `behaviorConfiguration`, Aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.  
  
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
  
 Varsayılan hizmet davranışı kümesinin hizmete eklendiğini unutmayın. Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaların paylaşmasına izin verir. Makine genelindeki kapsam gerekliyse, Machine.config bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App.config dosyalarında kullanılabilir. [Yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) , yapılandırmaların oluşturulmasını kolaylaştırır.  
  
## <a name="behavior-merge"></a>Davranış birleştirme  
 Davranış birleştirme özelliği, bir dizi ortak davranışın sürekli olarak kullanılmasını istediğinizde davranışları yönetmeyi kolaylaştırır. Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışlar belirtmenizi sağlar ve hizmetlerin, yapılandırma hiyerarşisinin birden fazla düzeyinden davranışları devralmasını sağlar. Bunun nasıl çalıştığını görmek için, IIS 'de aşağıdaki sanal dizin düzenine sahip olduğunu varsayın:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 Ve `~\Web.config` dosyanız aşağıdaki içeriğe sahiptir:  
  
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
  
 Ve aşağıdaki içeriklerle ~\Child\Web.config konumunda bulunan bir alt Web.config vardır:  
  
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
  
 Ayrıca, etiketini kullanarak \<clear> ve ' yi kullanarak tek davranışları koleksiyondan kaldırarak davranış koleksiyonlarını temizleyebilirsiniz \<remove> . Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca serviceMetadata davranışına sahip olmasına neden olur:  
  
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
  
 Davranış birleştirme, Web.config dosyalarının kök Web.config dosyası ve machine.config hiyerarşik olarak birleştirileyeceği IIS barındırma ortamında çalışmaktadır. Ancak, machine.config App.config dosyayla birleştirebildiği uygulama ortamında da kullanılır.  
  
 Davranış birleştirme, yapılandırma içindeki uç nokta davranışları ve hizmet davranışları için geçerlidir.  
  
 Bir alt davranış koleksiyonu, üst davranış koleksiyonunda zaten bulunan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar. Bu nedenle, bir üst davranış koleksiyonu `<serviceMetadata httpGetEnabled="False" />` ve bir alt davranış koleksiyonu varsa `<serviceMetadata httpGetEnabled="True" />` , alt davranış davranış koleksiyonundaki üst davranışı geçersiz kılar ve httpGetEnabled "true" olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](simplified-configuration.md)
- [WCF hizmetlerini yapılandırma](configuring-services.md)
- [\<service>](../configure-apps/file-schema/wcf/service.md)
- [\<binding>](../configure-apps/file-schema/wcf/bindings.md)
