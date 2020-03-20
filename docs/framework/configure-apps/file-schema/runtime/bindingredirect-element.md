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
ms.openlocfilehash: d96585b397f75dcb9fac7e7fce93799cc95e7c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154302"
---
# <a name="bindingredirect-element"></a>\<bağlayıcıRedirect> Elemanı
Bir derleme sürümünü diğerine yeniden yönlendirir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<montajBağlama>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bağımlıAssembly>**](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bağlayıcıRedirect>**  
  
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
|`oldVersion`|Gerekli öznitelik.<br /><br /> Başlangıçta istenen derleme sürümünü belirtir. Bir derleme sürüm numarasının biçimi *major.minor.build.revision*' dir. Bu sürüm numarasının her bir parçası için geçerli değerler 0 ile 65535 arasındadır.<br /><br /> Ayrıca, aşağıdaki biçimde bir sürüm aralığı da belirtebilirsiniz:<br /><br /> *n.n.n.n - n.n.n.n*|  
|`newVersion`|Gerekli öznitelik.<br /><br /> Biçimde başlangıçta istenen sürüm yerine kullanılacak derleme sürümünü belirtir: *n.n.n.n*<br /><br /> Bu değer, 'den `oldVersion`önceki bir sürümü belirtebilirsiniz.|  
  
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
 Kesin adlandırılmış bir derlemeye ilişkin olarak bir .NET Framework uygulaması oluşturduğunuzda, yeni bir sürüm kullanılabilir olsa bile, uygulama varsayılan olarak çalışma zamanında derlemenin o sürümünü kullanır. Bununla birlikte, uygulamayı derlemenin daha yeni bir sürümüne ilişkin olarak çalışacak şekilde yapılandırabilirsiniz. Çalışma zamanının hangi derleme sürümünü niçin kullanacağını belirlemek için bu dosyaları nasıl kullandığına ilişkin ayrıntılar [için, Çalışma Zamanı Derlemeleri Nasıl Bulur'a](../../../deployment/how-the-runtime-locates-assemblies.md)bakın.  
  
 Bir `bindingRedirect` `dependentAssembly` öğeye birden çok öğe ekleyerek birden fazla derleme sürümünü yeniden yönlendirebilirsiniz. Ayrıca, derlemenin daha yeni bir sürümünden daha eski bir sürümüne yeniden yönlendirme de yapabilirsiniz.  
  
 Bir uygulama yapılandırma dosyasında açık derleme bağlama yeniden yönlendirmesi için bir güvenlik izni gerekir. Bu, .NET Framework derlemelerinin ve üçüncü tarafların derlemelerinin yeniden yönlendirilmesi için geçerlidir. İzin, <xref:System.Security.Permissions.SecurityPermissionFlag> bayrağın üzerinde ayarlanmasıyla <xref:System.Security.Permissions.SecurityPermission>verilir. Daha fazla bilgi için, [Derleme Bağlama Yeniden Yönlendirme Güvenlik İzni'ne](../../assembly-binding-redirection-security-permission.md)bakın.  
  
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

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- [Bütünleştirilmiş Kod Sürümlerini Yönlendirme](../../redirect-assembly-versions.md)
