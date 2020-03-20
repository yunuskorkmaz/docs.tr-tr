---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: caf6e238ca286e5e712c0273e10502655fd7ff4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174803"
---
# <a name="configuring-services-using-configuration-files"></a>Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
Bir Windows Communication Foundation (WCF) hizmetini yapılandırma dosyasıyla yapılandırmak, tasarım zamanında değil, dağıtım noktasında uç nokta ve hizmet davranışı verileri sağlama esnekliği sağlar. Bu konu, kullanılabilir birincil teknikleri özetliyor.  
  
 Bir WCF hizmeti .NET Framework yapılandırma teknolojisi kullanılarak yapılandırılabilir. En yaygın olarak, Bir WCF hizmeti barındıran bir Internet Information Services (IIS) sitesi için Web.config dosyasına XML öğeleri eklenir. Öğeler, uç nokta adresleri (hizmetle iletişim kurmak için kullanılan gerçek adresler) gibi ayrıntıları makine bazında değiştirmenize olanak sağlar. Buna ek olarak, WCF hızlı bir hizmet için en temel özellikleri seçmek için izin birkaç sistem sağlanan öğeleri içerir. .NET Framework 4 ile başlayan WCF, WCF yapılandırma gereksinimlerini basitleştiren yeni bir varsayılan yapılandırma modeliyle birlikte gelir. Belirli bir hizmet için herhangi bir WCF yapılandırması sağlamazsanız, çalışma süresi hizmetinizi otomatik olarak bazı standart uç noktalar ve varsayılan bağlama/davranışla yapılandırır. Uygulamada, yapılandırma yazma WCF uygulamaları programlama önemli bir parçasıdır.  
  
 Daha fazla bilgi için, [Hizmetler için Bağlamaları Yapılandırma'ya](configuring-bindings-for-wcf-services.md)bakın. En sık kullanılan öğelerin listesi için [Sistem Tarafından Sağlanan Bağlamalar](system-provided-bindings.md)bölümüne bakın. Varsayılan uç noktalar, bağlamalar ve davranışlar hakkında daha fazla bilgi için wcf hizmetleri için [Basitleştirilmiş Yapılandırma](simplified-configuration.md) ve [Basitleştirilmiş Yapılandırma'ya](./samples/simplified-configuration-for-wcf-services.md)bakın.  
  
> [!IMPORTANT]
> Bir hizmetin iki farklı sürümü dağıtılan yan yana senaryoları dağıtırken, yapılandırma dosyalarında başvurulan derlemelerin kısmi adlarını belirtmek gerekir. Bunun nedeni, yapılandırma dosyasının bir hizmetin tüm sürümlerinde paylaşılması ve .NET Framework'ün farklı sürümleri altında çalışıyor olmalarıdır.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config ve App.config  
 WCF,.NET Framework'ün System.Configuration yapılandırma sistemini kullanır.  
  
 Visual Studio'da bir hizmeti yapılandırırken, ayarları belirtmek için bir Web.config dosyası veya App.config dosyası kullanın. Yapılandırma dosya adının seçimi, hizmet için seçtiğiniz barındırma ortamına göre belirlenir. Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web.config dosyası kullanın. Başka bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.  
  
 Visual Studio'da, App.config adlı dosya son yapılandırma dosyasını oluşturmak için kullanılır. Yapılandırma için kullanılan son ad derleme adına bağlıdır. Örneğin, "Cohowinery.exe" adlı bir derlemenin "Cohowinery.exe.config" son yapılandırma dosya adı vardır. Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir. Bu dosyada yapılan değişiklikler, derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.  
  
 App.config kullanarak, yapılandırma sistemi uygulama başlatıldığında ve yapılandırma uygulandığında App.config dosyasını Machine.config dosyasının içeriğiyle birleştirir. Bu mekanizma, Makine.config dosyasında makine genelinde ayarların tanımlanmasını sağlar. App.config dosyası Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; machine.config dosyasındaki ayarları da kilitleyebilir, böylece kullanılabilirler. Web.config durumunda, yapılandırma sistemi, uygulama dizinine giden tüm dizinlerde Web.config dosyalarını uygulanan yapılandırmayla birleştirir. Yapılandırma ve ayar öncelikleri hakkında daha fazla bilgi <xref:System.Configuration> için ad alanındaki konulara bakın.  
  
## <a name="major-sections-of-the-configuration-file"></a>Yapılandırma Dosyasının Ana Bölümleri  
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
> Bağlamalar ve davranışbölümleri isteğe bağlıdır ve yalnızca gerekirse dahildir.  
  
### <a name="the-services-element"></a>\<Hizmetler> Öğesi  
 Öğe, `services` uygulamanın barındırılacak tüm hizmetlerinin belirtimlerini içerir. .NET Framework 4'teki basitleştirilmiş yapılandırma modelinden başlayarak bu bölüm isteğe bağlıdır.  
  
 [\<hizmetler>](../configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>Hizmet \<> Öğesi  
 Her hizmetin şu öznitelikleri vardır:  
  
- `name`. Hizmet sözleşmesinin uygulanmasını sağlayan türü belirtir. Bu, ad alanı, bir dönem ve daha sonra tür adı oluşan tam nitelikli bir addır. Örneğin, `"MyNameSpace.myServiceType"`.  
  
- `behaviorConfiguration`. `behaviors` Öğede bulunan `behavior` öğelerden birinin adını belirtir. Belirtilen davranış, hizmetin kimliğe bürünme izin verip vermediği gibi eylemleri yönetir. Değeri boş adsa veya `behaviorConfiguration` hiç sağlanmışsa, varsayılan hizmet davranışı kümesi hizmete eklenir.  
  
- [\<hizmet>](../configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>Bitiş \<Noktası> Öğesi  
 Her bitiş noktası, aşağıdaki özniteliklerle temsil edilen bir adres, bağlama ve sözleşme gerektirir:  
  
- `address`. Hizmetin mutlak bir adres veya hizmetin temel adresine göre verilen tek düzen kaynak tanımlayıcısını (URI) belirtir. Boş bir dize olarak ayarlanırsa, hizmet için oluştururken belirtilen temel <xref:System.ServiceModel.ServiceHost> adreste bitiş noktasının kullanılabilir olduğunu gösterir.  
  
- `binding`. Genellikle, sistem tarafından sağlanan bir <xref:System.ServiceModel.WSHttpBinding>bağlama gibi belirtir, ancak kullanıcı tanımlı bir bağlama da belirtebilir. Belirtilen bağlama, kullanılan aktarım, güvenlik ve kodlama türünü ve güvenilir oturumların, hareketlerin veya akışların desteklenip desteklenmediğini veya etkinleştirilip etkinleştirilemeyeceğini belirler.  
  
- `bindingConfiguration`. Bir bağlamanın varsayılan değerlerinin değiştirilmesi gerekiyorsa, bu `binding` `bindings` öğedeki uygun öğe yi yapılandırarak yapılabilir. Bu öznitelik, varsayılanları değiştirmek `name` için kullanılan `binding` öğenin özniteliği ile aynı değer verilmelidir. Hiçbir ad verilmezveya bağlamada belirtilmemişse, `bindingConfiguration` bitiş noktasında bağlama türünün varsayılan bağlaması kullanılır.  
  
- `contract`. Sözleşmeyi tanımlayan arabirimi belirtir. Bu, `service` öğenin özniteliği tarafından belirtilen ortak dil çalışma süresi `name` (CLR) türünde uygulanan arabirimdir.  
  
- [\<bitiş noktası>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>Bağlamalar \<> Öğesi  
 Öğe, `bindings` herhangi bir hizmette tanımlanan herhangi bir uç nokta tarafından kullanılabilecek tüm bağlamaların belirtimlerini içerir.  
  
 [\<>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Bağlayıcı> Öğesi  
 Öğede bulunan `binding` öğeler, sistem tarafından sağlanan bağlamalardan biri [(bkz. Sistem Sağlanan Bağlamalar)](system-provided-bindings.md)veya özel bir bağlama olabilir (bkz. [Özel Bağlamalar).](./extending/custom-bindings.md) `bindings` Öğe, `binding` öğenin özniteliği belirtilen `name` `bindingConfiguration` bitiş noktası ile bağlama ilişkilendiren bir `endpoint` öznitelik vardır. Hiçbir ad belirtilmemişse, bu bağlama bu bağlama türünün varsayılanına karşılık gelir.  
  
Hizmetleri ve istemcileri yapılandırma hakkında daha fazla bilgi için [WCF hizmetlerini yapılandırma](configuring-services.md)ya da yapılandırma ya da geliştirme bilgisine bakın.
  
 [\<bağlayıcı>](../configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-behaviors-element"></a>> \<Davranışları  
 Bu, bir hizmetin `behavior` davranışlarını tanımlayan öğeler için bir kapsayıcı öğesidir.  
  
 [\<davranışlar>](../configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>Davranış \<> Öğesi  
 Her `behavior` öğe bir `name` öznitelik tarafından tanımlanır ve <`throttling`> gibi sistem tarafından sağlanan bir davranış veya özel bir davranış sağlar. Ad verilmezse, bu davranış öğesi varsayılan hizmete veya bitiş noktası davranışına karşılık gelir.  
  
 [\<davranış>](../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Bağlama ve Davranış Yapılandırmaları Nasıl Kullanılır?  
 WCF yapılandırmada bir başvuru sistemi kullanarak son noktalar arasında yapılandırmaları paylaşmayı kolaylaştırır. Yapılandırma değerlerini doğrudan bir uç noktaya atamak yerine, bağlamayla `bindingConfiguration` ilgili yapılandırma `<binding>` değerleri bölümdeki öğelerde gruplandırılır. Bağlayıcı yapılandırma, bağlama üzerinde adlandırılmış bir ayar grubudur. Uç noktalar daha `bindingConfiguration` sonra ada göre başvuruda bulunabilir.  
  
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
  
 Öğenin `name` `bindingConfiguration` kümesi öğede `<binding>` ayarlanır. Bağlama `name` türü kapsamında benzersiz bir dize olmalıdır—bu durumda [<temelHttpBinding\>](../configure-apps/file-schema/wcf/basichttpbinding.md)veya varsayılan bağlama başvurmak için boş bir değer. Bitiş noktası, bu dize `bindingConfiguration` özniteliği ayarlayarak yapılandırmaya bağlanır.  
  
 A, `behaviorConfiguration` aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.  
  
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
  
 Varsayılan hizmet davranışı kümesinin hizmete eklenmiştir. Bu sistem, uç noktaların ayarları yeniden tanımlamadan ortak yapılandırmaları paylaşmasına olanak tanır. Makine genelinde kapsam gerekiyorsa, Machine.config'de bağlama veya davranış yapılandırmasını oluşturun. Yapılandırma ayarları tüm App.config dosyalarında kullanılabilir. [Configuration Editor Aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md) yapılandırmaları oluşturmayı kolaylaştırır.  
  
## <a name="behavior-merge"></a>Davranış Birleştirme  
 Davranış birleştirme özelliği, ortak davranış lar kümesinin tutarlı bir şekilde kullanılmasını istediğinizde davranışların yönetilmesini kolaylaştırır. Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerinde davranışları belirtmenize ve hizmetlerin yapılandırma hiyerarşisinin birden çok düzeyinden davranışları devralmasına olanak tanır. Bu çalışmaların nasıl çalıştığını göstermek için IIS'de aşağıdaki sanal dizin düzenine sahip olduğunuzu varsayalım:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 Dosyanızda `~\Web.config` aşağıdaki içerikler vardır:  
  
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
  
 Ve bir çocuk Web.config bulunan ~\Child\Web.config aşağıdaki içeriği ile:  
  
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
  
 ~\Child\Service.svc adresinde bulunan hizmet, hem hizmetDebug hem de serviceMetadata davranışlarına sahipmiş gibi davranacaktır. ~\Service.svc adresinde bulunan hizmet yalnızca hizmet Hata Ayıklama davranışına sahip olacaktır. Ne olur, aynı ada sahip iki davranış koleksiyonları (bu durumda boş dize) birleştirilir.  
  
 Ayrıca, açık> etiketini \<kullanarak davranış koleksiyonlarını temizleyebilir ve \<kaldırma> etiketini kullanarak tek tek davranışları koleksiyondan kaldırabilirsiniz. Örneğin, aşağıdaki iki yapılandırma alt hizmetin yalnızca hizmetMetaveri davranışına sahip olmasıyla sonuçlanır:  
  
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
  
 Davranış birleştirme, yukarıda gösterildiği gibi adsız davranış koleksiyonları için de yapılır.  
  
 Davranış birleştirme, Web.config dosyalarının root Web.config dosyası ve machine.config ile hiyerarşik olarak birleştiği IIS barındırma ortamında çalışır. Ama aynı zamanda uygulama ortamında çalışır, burada machine.config App.config dosyası ile birleşebilir.  
  
 Davranış birleştirme yapılandırmada hem uç nokta davranışları hem de hizmet davranışları için geçerlidir.  
  
 Alt davranış koleksiyonu, üst davranış koleksiyonunda zaten mevcut olan bir davranış içeriyorsa, alt davranış üst öğeyi geçersiz kılar. Yani bir üst davranış `<serviceMetadata httpGetEnabled="False" />` koleksiyonu vardı ve `<serviceMetadata httpGetEnabled="True" />`bir alt davranış koleksiyonu vardı , alt davranış davranış koleksiyonunda üst davranışı geçersiz kılar ve httpGetEnabled "doğru" olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](simplified-configuration.md)
- [WCF hizmetlerinin yapılandırılması](configuring-services.md)
- [\<hizmet>](../configure-apps/file-schema/wcf/service.md)
- [\<bağlayıcı>](../configure-apps/file-schema/wcf/bindings.md)
