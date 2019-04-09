---
title: Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 144d2b6732ea319ba920317601eff2ebd7b58322
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132580"
---
# <a name="configuring-services-using-configuration-files"></a>Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
Bir yapılandırma dosyası bir Windows Communication Foundation (WCF) hizmetini yapılandırma uç noktası sağlama esnekliği sunar ve hizmet davranışı veri yerine dağıtım noktasında tasarım. Bu konu, birincil teknikleri açıklar.  
  
 Bir WCF Hizmeti yapılandırılabilir kullanmaktır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknoloji. En yaygın olarak, XML öğeleri, bir WCF hizmetini barındıran Internet Information Services (IIS) sitesi için Web.config dosyasına eklenir. Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin. Ayrıca, WCF, hızlı bir şekilde bir hizmet için en temel özellikler seçmenizi sağlayacak birçok sistem tarafından sağlanan öğeleri içerir. İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF, WCF yapılandırma gereksinimleri basitleştiren yeni bir varsayılan yapılandırma modeli ile birlikte gelir. Belirli bir hizmet için herhangi bir WCF yapılandırma sağlamazsanız, çalışma zamanının bazı standart uç noktalar ve varsayılan bağlama/davranışı ile otomatik olarak hizmetinizi yapılandırır. Büyük bir uygulamada, yazma yapılandırmadır WCF uygulamalarını programlama parçası.  
  
 Daha fazla bilgi için [hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). Yaygın olarak kullanılan öğeleri en listesi için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md). Varsayılan uç noktaları, bağlamalar ve davranışları hakkında daha fazla bilgi için bkz. [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Dağıtıldığı bir hizmeti iki farklı sürümlerini yan yana senaryoları dağıtırken, yapılandırma dosyalarında başvurulan derlemeleri kısmi adını belirtmek gereklidir. Yapılandırma dosyası, bir hizmetin tüm sürümleri arasında paylaşılır ve altında .NET Framework'ün farklı sürümlerini çalıştıran çünkü budur.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config ve App.config  
 WCF kullanan System.Configuration yapılandırma sistemi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Bir hizmet Visual Studio'da yapılandırırken, Web.config dosyası veya bir App.config dosyası ayarlarını belirtmek için kullanın. Yapılandırma dosyası adı seçimi hizmeti için seçtiğiniz barındırma ortamı tarafından belirlenir. Hizmetinizi barındırmak için IIS kullanıyorsanız, Web.config dosyasını kullanın. Herhangi bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.  
  
 Visual Studio'da App.config adlı dosyayı son yapılandırma dosyası oluşturmak için kullanılır. Son adı gerçekte yapılandırma için kullanılan derleme adına bağlıdır. Örneğin, "Cohowinery.exe" adlı bir derleme "Cohowinery.exe.config" son yapılandırma dosya adı vardır. Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir. Bu dosyada yapılan değişiklikler, derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.  
  
 Kullanarak bir App.config dosyası yapılandırma sistemi Machine.config dosyasının içeriğini App.config dosyanızı uygulama başladığında ve yapılandırmanın uygulanması birleştirir. Bu mekanizma, makine genelindeki ayarlarının Machine.config dosyasında tanımlıdır sağlar. App.config dosyası, Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; böylece bunlar alışmanız Machine.config dosyasının ayarlarında kilitleyebilirsiniz. Web.config durumda yapılandırma sistemi, uygulanan yapılandırmaya uygulama dizinine öncesinde tüm dizinleri Web.config dosyalarında birleştirir. Yapılandırma ve ayarlama öncelikleri hakkında daha fazla bilgi için bkz <xref:System.Configuration> ad alanı.  
  
## <a name="major-sections-of-the-configuration-file"></a>Yapılandırma dosyasının ana bölümlerinin  
 Ana bölümleri yapılandırma dosyasında aşağıdaki öğeleri içerir.  
  
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
>  Bağlamalar ve davranışları bölümler isteğe bağlıdır ve bu yalnızca gerekirse dahil.  
  
### <a name="the-services-element"></a>\<Hizmetleri > öğesi  
 `services` Öğesi tüm hizmetleri uygulama konakları için özellikleri içerir. Basitleştirilmiş yapılandırma modeli ile başlayan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu bölüm isteğe bağlıdır.  
  
 [\<Hizmetleri >](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<Hizmet > öğesi  
 Her hizmet bu özniteliklere sahiptir:  
  
-   `name`biçimindeki telefon numarasıdır. Bir hizmet sözleşmesinin bir uygulaması sağlayan bir tür belirtir. Bu ad, nokta ve tür adı sonra oluşan tam bir addır. Örneğin `"MyNameSpace.myServiceType"`.  
  
-   `behaviorConfiguration`biçimindeki telefon numarasıdır. Birinin adını belirten `behavior` öğeleri bulunan `behaviors` öğesi. Belirtilen davranışını hizmete bürünme izin verip gibi eylemleri yönetir. Öğenin değeri adı boş veya yok ise `behaviorConfiguration` hizmet davranışları varsayılan kümesi için hizmet eklendikten sonra sağlanır.  
  
-   [\<Hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<Uç noktası > öğesi  
 Bir adresi, bağlama ve bir sözleşme aşağıdaki öznitelikleri tarafından temsil edilen her uç nokta gerektirir:  
  
-   `address`biçimindeki telefon numarasıdır. Hizmetin Tekdüzen Kaynak Tanımlayıcısı (URI), mutlak bir adres veya hizmetin taban adresi göre verilen bir olabilen belirtir. Boş dize olarak ayarlanırsa, bu uç nokta oluşturulurken belirtilen temel adresinde kullanılabilir olduğunu gösterir, <xref:System.ServiceModel.ServiceHost> hizmeti.  
  
-   `binding`biçimindeki telefon numarasıdır. Genellikle gibi sistem tarafından sağlanan bir bağlamayı belirtir <xref:System.ServiceModel.WSHttpBinding>, ancak kullanıcı tanımlı bir bağlama de belirtebilirsiniz. Belirtilen bağlama türü taşıma, güvenlik ve kodlamayı belirler ve olup güvenilir oturumlar, işlemler veya akış desteklenen etkin veya.  
  
-   `bindingConfiguration`biçimindeki telefon numarasıdır. Bağlama varsayılan değerlerinin değiştirilmesi gerekir, bu uygun yapılandırarak yapılabilir `binding` öğesinde `bindings` öğesi. Bu öznitelik aynı değere verilmelidir `name` özniteliği `binding` varsayılan değerleri değiştirmek için kullanılan bir öğe. Ad belirtilmezse, ya da hiç `bindingConfiguration` bağlamasında belirtilen bağlama türü varsayılan bağlamasının uç noktasında kullanılır.  
  
-   `contract`biçimindeki telefon numarasıdır. Sözleşme tanımlayan arabirimi belirtir. Bu tarafından belirtilen ortak dil çalışma zamanı (CLR) türüne uygulanan arabirimidir `name` özniteliği `service` öğesi.  
  
-   [\<uç noktası >](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a>\<Bağlamaları > öğesi  
 `bindings` Öğesi herhangi bir hizmette tanımlanan herhangi bir uç nokta tarafından kullanılan tüm bağlamaları için özellikleri içerir.  
  
 [\<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Bağlama > öğesi  
 `binding` İçindeki öğe `bindings` öğesi, sistem tarafından sağlanan bağlamalar birini olabilir (bakın [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)) veya özel bir bağlama (bkz [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md)). `binding` Öğeye sahip bir `name` belirtilen uç noktası ile bağlama karşılık gelen öznitelik `bindingConfiguration` özniteliği `endpoint` öğesi. Bu bağlama varsayılan bağlama türü için karşılık gelen sonra hiçbir ad belirtilmezse.  
  
Hizmetler ve istemcileri yapılandırma hakkında daha fazla bilgi için bkz. [yapılandırma WCF hizmetleri](configuring-services.md).
  
 [\<bağlama >](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<Davranışları > öğesi  
 İçin bir kapsayıcı öğe budur `behavior` bir hizmet için davranışları tanımlayan öğeler.  
  
 [\<davranışlar >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Davranışı > öğesi  
 Her `behavior` öğesi tarafından tanımlanan bir `name` özniteliği ve ya da bir sistem tarafından sağlanan, gibi sağlar <`throttling`>, ya da özel bir davranış. Adsız verilirse, bu davranış öğesi varsayılan hizmet veya uç nokta davranışı karşılık gelir.  
  
 [\<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Bağlama ve davranışı yapılandırmaları kullanma  
 WCF yapılandırmaları yapılandırmasında bir başvuru sistemi kullanarak uç noktalar arasında paylaşmak kolaylaştırır. Yapılandırma değerleri bir uç noktaya doğrudan atamak yerine, bağlama ile ilgili yapılandırma değerleri olarak gruplandırılır `bindingConfiguration` öğelerinde `<binding>` bölümü. Bir bağlama yapılandırmasını, bağlama ayarları, adlandırılmış bir gruptur. Uç noktaları sonra başvuruda `bindingConfiguration` ada göre.  
  
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
  
 `name` , `bindingConfiguration` Ayarlanır `<binding>` öğesi. `name` Bağlama türü kapsamında benzersiz bir dize olmalıdır; bu durumda [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), ya da varsayılan bağlama başvurmak için boş bir değer. Uç nokta bağlantılar ayarlayarak yapılandırmayı `bindingConfiguration` için bu dize özniteliği.  
  
 A `behaviorConfiguration` aşağıdaki örnekte gösterildiği gibi aynı şekilde uygulanır.  
  
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
  
 Hizmet davranışları varsayılan kümesini hizmete eklenir unutmayın. Bu sistem ayarları yeniden tanımlama olmadan yapılandırmaların paylaşmak uç noktaları sağlar. Makine genelinde kapsam gerekiyorsa, Machine.config dosyasına bağlama veya davranışını yapılandırma oluşturun. Yapılandırma ayarları tüm App.config dosyalarında kullanılabilir. [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) yapılandırmaları oluşturmayı kolaylaştırır.  
  
## <a name="behavior-merge"></a>Birleştirme davranışı  
 Davranış birleştirme özelliği, bir dizi ortak davranışları sürekli olarak kullanılacak istediğinizde davranışları yönetmek üzere kolaylaştırır. Bu özellik, farklı düzeylerde yapılandırma hiyerarşisinin davranışları belirtin ve birden çok yapılandırma hiyerarşi düzeylerinden davranışları devral hizmetleri sağlar. Göstermek için nasıl bu çalışır sahip olduğunuzu varsayar şu sanal dizin Düzen IIS içinde:  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 Ve `~\Web.config` dosya aşağıdaki içeriğe sahip:  
  
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
  
 Ve aşağıdaki içeriklerle ~\Child\Web.config Web.config konumundaki bir alt sahip:  
  
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
  
 ~\Child\Service.svc bulunan hizmet serviceDebug ve serviceMetadata davranışlarını içermese gibi davranır. ~\Service.svc bulunan hizmet yalnızca serviceDebug davranışa sahip olur. (Bu örnekte boş bir dize) aynı ada sahip iki davranışı koleksiyonlar birleştirilmeden olur.  
  
 Davranış koleksiyonlarını kullanarak da temizleyebilirsiniz \<Temizle > etiketi ve tek tek davranışları kullanarak koleksiyondan kaldırılır \<kaldırmak > etiketi. Örneğin, yalnızca serviceMetadata davranışı sahip alt aşağıdaki iki yapılandırma sonuçları hizmeti:  
  
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
  
 Davranış birleştirme yukarıda da gösterildiği gibi adsız davranışı koleksiyonlar için yapılan ve davranış koleksiyonları adlı.  
  
 IIS barındırma ortamında machine.config ve kök Web.config dosyasında ile hiyerarşik olarak Web.config dosyaları birleştirme davranışı birleştirme çalışır. Ancak, machine.config App.config dosyanızı nereye birleştirebilirsiniz uygulama ortamda çalışır.  
  
 Uç nokta davranışları hem yapılandırma hizmet davranışları birleştirme davranışı uygular.  
  
 Bir alt davranışı koleksiyon üst davranışı koleksiyonda zaten var. bir davranış içeriyorsa, üst alt davranışı geçersiz kılar. Üst davranışı koleksiyonu varsa bunu `<serviceMetadata httpGetEnabled="False" />` ve alt davranışı koleksiyonunu `<serviceMetadata httpGetEnabled="True" />`, alt davranışı, davranış koleksiyondaki üst öğe davranışı geçersiz kılarsınız ve de "true" olacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Basitleştirilmiş Yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)
- [WCF hizmetlerini yapılandırma](configuring-services.md)
- [\<Hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)
- [\<bağlama >](../../../docs/framework/misc/binding.md)
