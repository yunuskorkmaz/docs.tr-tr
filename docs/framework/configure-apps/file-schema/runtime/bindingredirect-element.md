---
title: <bindingRedirect> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
ms.openlocfilehash: dda99bb4b96efbdd274e24e7cd548e4ed4df8b66
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704901"
---
# <a name="bindingredirect-element"></a>\<bindingRedirect > öğesi
Bir derleme sürümünü diğerine yeniden yönlendirir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<assemblyBinding >  
\<dependentAssembly >  
\<bindingRedirect >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`oldVersion`|Gerekli öznitelik.<br /><br /> Başlangıçta istenen derleme sürümünü belirtir. Bir derleme sürümü numarasının biçimi *major.minor.build.revision*. Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.<br /><br /> Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Gerekli öznitelik.<br /><br /> Biçimde başlangıçta istenen sürüm yerine kullanılacak derleme sürümünü belirtir: *n.n.n.n*<br /><br /> ' Den önceki sürümleri bu değeri belirtebilirsiniz `oldVersion`.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`assemblyBinding`|Derleme sürümü yeniden yönlendirmesi ve derlemelerin konumları hakkında bilgi içerir.|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`dependentAssembly`|Her bir derleme için bağlama ilkesi ve derleme konumunu saklar. Her bir derleme için bir bağımlı Derleme öğesi kullanın.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır. Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz. Bu dosyalarını çalışma zamanının hangi derleme sürümünün kullanılacağını belirlemek için nasıl kullandığı hakkında daha fazla bilgi için bkz [çalışma zamanı derlemeleri nasıl konumlandırır](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Ekleyerek, birden çok derleme sürümünü yeniden yönlendirebilirsiniz `bindingRedirect` öğelerinde bir `dependentAssembly` öğesi. Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.  
  
 Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir. Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir. İzin ayarlanarak verilir <xref:System.Security.Permissions.SecurityPermissionFlag> üzerinde bayrak <xref:System.Security.Permissions.SecurityPermission>. Daha fazla bilgi için [bütünleştirilmiş kod bağlama yönlendirmesi güvenlik izni](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir derleme sürümünün diğerine nasıl yeniden yönlendirileceği gösterilmiştir.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
