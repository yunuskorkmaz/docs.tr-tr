---
title: "Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 480cdb83248dc1cf9dd90c0f654aa4f269318c4a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="configuring-services-using-configuration-files"></a>Yapılandırma Dosyalarını Kullanarak Hizmetleri Yapılandırma
Yapılandırma bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmeti bir yapılandırma dosyası ile tasarım zamanında yerine dağıtım noktasında uç noktası ve hizmet davranışı verileri sağlayan esnekliği sağlar. Bu konu, birincil teknikleri özetler.  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmetidir yapılandırılabilir kullanarak [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] yapılandırma teknolojisi. XML öğeleri barındıran Internet Information Services (IIS) sitesi için Web.config dosyasının en yaygın olarak eklenen bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet. Öğeleri, uç nokta adresleri (hizmetiyle iletişim kurmak için kullanılan gerçek adresleri) gibi ayrıntılarını değiştirmek bir makine Makineli temelinde izin verin. Ayrıca, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hızlı bir şekilde bir hizmeti için en temel özellikleri seçmenize olanak birkaç sistem tarafından sağlanan öğeleri içerir. İle başlayarak [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kolaylaştıran yeni bir varsayılan yapılandırma modeli ile birlikte gelen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yapılandırma gereksinimleri. Herhangi bir sağlamazsanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] yapılandırma çalışma zamanı belirli bir hizmet için bazı standart uç noktaları ve varsayılan bağlama/davranışı hizmetinizi otomatik olarak yapılandırır. Uygulamada, yazma yapılandırma programlama önemli bir parçası olan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar.  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hizmetler için bağlamaları yapılandırma](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md). [!INCLUDE[crlist](../../../includes/crlist-md.md)]en yaygın kullanılan öğeler bkz [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]Varsayılan uç noktalar, bağlamaları ve davranışları, bkz: [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md) ve [WCF hizmetleri için Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Bir hizmeti iki farklı sürümü dağıtıldığı yan yana senaryoları dağıtırken, yapılandırma dosyalarını başvurulan derlemelerin kısmi adını belirtmek gereklidir. Bu yapılandırma dosyası, bir hizmetin tüm sürümleri arasında paylaşılır ve altında .NET Framework'ün farklı sürümlerini çalıştıran kaynaklanır.  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a>System.Configuration: Web.config ve App.config  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]System.Configuration yapılandırma sistemini kullanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Bir hizmet olarak yapılandırırken [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], bir Web.config dosyası veya bir App.config dosyası ayarlarını belirtmek için kullanın. Yapılandırma dosyasının adını seçimi hizmeti için seçtiğiniz barındırma ortamı tarafından belirlenir. Hizmetinizi barındırmak için IIS kullanıyorsanız, bir Web.config dosyası kullanın. Herhangi bir barındırma ortamı kullanıyorsanız, bir App.config dosyası kullanın.  
  
 İçinde [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], App.config adlı dosyayı son yapılandırma dosyası oluşturmak için kullanılır. Gerçekte yapılandırma için kullanılan son adı derleme adına bağlıdır. Örneğin, "Cohowinery.exe" adlı bir derleme "Cohowinery.exe.config" bir son yapılandırma dosya adına sahip. Ancak, yalnızca App.config dosyasını değiştirmeniz gerekir. Bu dosyada yapılan değişiklikler, derleme zamanında son uygulama yapılandırma dosyasına otomatik olarak yapılır.  
  
 Kullanarak bir App.config dosyası yapılandırma sistemi App.config dosyası Machine.config dosyasının içeriği ile uygulama başlar ve yapılandırmanın uygulanması birleştirir. Bu mekanizma Machine.config dosyasında tanımlanmış için makine genelinde ayarlarını sağlar. App.config dosyasını Machine.config dosyasının ayarlarını geçersiz kılmak için kullanılabilir; Böylece kullanılan Machine.config dosyasının ayarlarında kilitleyebilirsiniz. Web.config durumda uygulama dizinine uygulanan yapılandırmaya baştaki tüm dizinleri Web.config dosyalarında yapılandırma sistemi birleştirir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Yapılandırma ve ayarı öncelikleri bkz konularında <xref:System.Configuration> ad alanı.  
  
## <a name="major-sections-of-the-configuration-file"></a>Yapılandırma dosyasının ana bölümleri  
 Yapılandırma dosyasındaki ana bölümleri aşağıdaki öğeleri içerir.  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
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
>  Bağlamalar ve davranışları bölümler isteğe bağlı olan ve bu gerekli olursa yalnızca.  
  
### <a name="the-services-element"></a>\<Hizmetleri > öğesi  
 `services` Öğesi tüm hizmetleri uygulama konakları özelliklerini içerir. Basitleştirilmiş yapılandırma modele itibaren [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bu bölümde isteğe bağlıdır.  
  
 [\<Hizmetleri >](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a>\<Hizmet > öğesi  
 Her hizmet bu özniteliklere sahiptir:  
  
-   `name`. Bir hizmet sözleşmesini uygulaması sağlar türünü belirtir. Bu ad, bir süre ve tür adı sonra oluşan tam bir addır. Örneğin `"MyNameSpace.myServiceType"`.  
  
-   `behaviorConfiguration`. Birinin adını belirtir `behavior` öğeleri bulunan `behaviors` öğesi. Belirtilen davranışını hizmet kimliğe bürünme izin verip gibi eylemleri yönetir. Öğenin değeri adı boş veya Hayır ise `behaviorConfiguration` hizmet davranışları varsayılan kümesini hizmete eklendikten sonra sağlanır.  
  
-   [\<Hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a>\<Uç noktası > öğesi  
 Bir adresi, bağlama ve bir sözleşme aşağıdaki öznitelikleri tarafından temsil edilen her uç nokta gerektiriyor:  
  
-   `address`. Hizmetin Tekdüzen Kaynak Tanımlayıcısı (URI), mutlak bir adres veya hizmetin taban adresi göre verilen biri olabilen belirtir. Boş bir dize olarak ayarlandıysa, bu uç noktası oluşturulurken belirtilen temel adresinde kullanılabilir olduğunu gösterir <xref:System.ServiceModel.ServiceHost> hizmeti.  
  
-   `binding`. Genellikle gibi sistem tarafından sağlanan bir bağlamayı belirtir <xref:System.ServiceModel.WSHttpBinding>, ancak kullanıcı tanımlı bir bağlama de belirtebilirsiniz. Belirtilen bağlama taşıma, güvenlik ve kullanılan kodlama türünü belirler ve güvenilir oturumlar, işlemler veya akış desteklenen etkin mı.  
  
-   `bindingConfiguration`. Varsayılan değerleri bağlaması değiştirilmesi gerekir, bu uygun yapılandırarak yapılabilir `binding` öğesinde `bindings` öğesi. Bu öznitelik ile aynı değere verilmelidir `name` özniteliği `binding` varsayılanları değiştirmek için kullanılan öğesi. Ad belirtilmezse ya da hiç `bindingConfiguration` bağlama türü varsayılan bağlamasının uç kullanılır bağlamasında belirtilir.  
  
-   `contract`. Sözleşmesini tanımlayan arabirimi belirtir. Bu tarafından belirtilen ortak dil çalışma zamanı (CLR) türüne uygulanan arabirimidir `name` özniteliği `service` öğesi.  
  
-   [\<uç noktası > öğesi başvurusu](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a>\<Bağlamaları > öğesi  
 `bindings` Öğesi içinde herhangi bir hizmeti tanımlanan herhangi bir uç nokta tarafından kullanılan tüm bağlamaları özelliklerini içerir.  
  
 [\<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a>\<Bağlama > öğesi  
 `binding` İçindeki öğe `bindings` öğesi, sistem tarafından sağlanan bağlamalar birini olabilir (bakın [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md)) veya özel bağlama (bkz [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md)). `binding` Öğeye sahip bir `name` belirtilen uç noktası ile bağlama karşılık gelen öznitelik `bindingConfiguration` özniteliği `endpoint` öğesi. Bu bağlama, bağlama türü varsayılan olarak karşılık gelen sonra ad belirtilmezse.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Hizmetler ve istemcileri yapılandırmak, bkz: [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
 [\<bağlama >](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a>\<Davranışları > öğesi  
 Bu kapsayıcı için bir unsurdur `behavior` bir hizmet için davranışları tanımlamak öğeleri.  
  
 [\<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a>\<Davranışı > öğesi  
 Her `behavior` öğesi tarafından tanımlanan bir `name` özniteliği ve ya da bir sistem tarafından sağlanan davranışı gibi sağlar <`throttling`>, veya özel bir davranış. Ad belirtilmezse bu davranışı öğesi varsayılan hizmet veya uç noktası davranışı karşılık gelir.  
  
 [\<davranışı >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a>Bağlama ve davranış yapılandırmalarını kullanma  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]yapılandırmaları başvuru sistemi yapılandırmayla uç noktalar arasında paylaşmak kolaylaştırır. Yapılandırma değerlerini bir bitiş noktasına doğrudan atamak yerine, bağlama ile ilgili yapılandırma değerlerini gruplandırılmıştır `bindingConfiguration` öğelerinde `<binding>` bölümü. Bağlama yapılandırması, bir bağlama ayarlarını adlandırılmış grubudur. Uç noktalar sonra başvuru `bindingConfiguration` ada göre.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
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
  
 `name` , `bindingConfiguration` Kümesinde `<binding>` öğesi. `name` Bağlama türü kapsamında benzersiz bir dize olması gerekir; bu durumda [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), ya da varsayılan bağlama başvurmak için boş bir değer. Uç noktası bağlantıları ayarlayarak yapılandırma `bindingConfiguration` özniteliği bu dize.  
  
 A `behaviorConfiguration` aynı şekilde, aşağıdaki örnekte gösterildiği gibi uygulanır.  
  
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
  
 Hizmet davranışları varsayılan kümesini hizmetine eklendiğinde unutmayın. Bu sistem ayarlarını tanımlayarak olmadan ortak yapılandırmaları paylaşmak uç noktaları sağlar. Makine genelinde kapsam gerekiyorsa, bağlama veya davranışını yapılandırma Machine.config içinde oluşturun. Yapılandırma ayarları tüm App.config dosyaları kullanılabilir. [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) yapılandırmaları oluşturmak kolay hale getirir.  
  
## <a name="behavior-merge"></a>Davranış birleştirme  
 Davranış birleştirme özelliği, sürekli olarak kullanılacak ortak davranışları kümesi istediğinizde davranışlarını yönetmek üzere kolaylaştırır. Bu özellik, yapılandırma hiyerarşisinin farklı düzeylerde davranışları belirtmek ve Hizmetleri, birden çok yapılandırma hiyerarşisini düzeylerinden davranışları devralmak sağlar. Göstermek için nasıl bu works sahip olduğunuzu varsayar aşağıdaki sanal dizin düzeni IIS'de:  
  
 ~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc  
  
 Ve ~\Web.config dosyanız aşağıdaki içeriğe sahip:  
  
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
  
 Ve Web.config aşağıdaki içeriğe sahip ~\Child\Web.config konumunda bulunan alt vardır:  
  
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
  
 ~\Child\Service.svc bulunan hizmet serviceDebug ve serviceMetadata davranışları içermese gibi davranır. ~\Service.svc bulunan hizmet serviceDebug davranışı yalnızca sahip olur. (Bu durumda boş dize) aynı ada sahip iki davranış koleksiyonları birleştirilir olur.  
  
 Kullanarak davranış koleksiyonları temizleyebilirsiniz \<temizleyin > etiketi ve kullanarak tek tek davranışları koleksiyondan kaldırıldı \<kaldırma > etiketi. Örneğin, aşağıdaki iki yapılandırma sonuçlarında alt yalnızca serviceMetadata davranışı sahip hizmeti:  
  
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
  
 Davranış birleştirme yukarıda gösterildiği gibi adsız davranışı koleksiyonlar için yapılan ve davranış koleksiyonları adlı.  
  
 Davranış birleştirme ortamında hangi Web.config dosyaları birleştirme hiyerarşik olarak machine.config ve kök Web.config dosyasında barındıran IIS çalışır. Ancak, uygulama ortamında machine.config App.config dosyası ile burada birleştirebilirsiniz çalışır.  
  
 Uç nokta davranışları ve hizmet davranışları yapılandırma davranışı birleştirme uygular.  
  
 Bir alt davranışı koleksiyon üst davranışı koleksiyonda zaten bir davranış içeriyorsa, alt davranışı üst geçersiz kılar. Bir üst davranışı koleksiyon sahipse, bu nedenle `<serviceMetadata httpGetEnabled="False" />` ve alt davranışı koleksiyonunu `<serviceMetadata httpGetEnabled="True" />`, alt davranışı davranışı koleksiyonundaki üst davranışı geçersiz kılarsınız ve de "true" olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Basitleştirilmiş yapılandırma](../../../docs/framework/wcf/simplified-configuration.md)  
 [Windows Communication Foundation uygulamaları yapılandırma](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [\<Hizmet >](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [\<bağlama >](../../../docs/framework/misc/binding.md)
