---
title: x:Property Yönergesi
ms.date: 03/30/2017
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
ms.openlocfilehash: ab25381769e7001f7f48d73e717b5f495da90dfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796454"
---
# <a name="xproperty-directive"></a>x:Property Yönergesi
Biçimlendirme XAML özelliğinde bildirir.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Property Name="propertyName" Type="propertyType/>  
    additionalProperties  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`className`|XAML üretim için yedekleme sınıf veya kısmi sınıf adıdır.|  
|`propertyName`|Tanımlanan özellik üyesinin adı.|  
|`propertyType`|Tür adı (veya çerçeveye özgü diğer dize biçiminde), bu özelliğin türünü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML hizmetlerinde uygulamasında. `x:Property` Yedekleme doğrudan bir türün yok, ancak tarafından desteklenen <xref:System.Windows.Markup.PropertyDefinition> sınıfı. XAML düğüm akış bir `x:Property` öğesi adlı bir üyesi olarak temsil edilir `Property`, XAML dili XAML ad uzayındaki. Üye `Property` biçimlendirme tarafından bildirilen gibi öznitelikleri tutun.  
  
 Anlamını `Name` ve `Type` .NET Framework XAML hizmetlerinde düzeyinde atanmaz. Daha sonra belirli çerçeveleri tarafından uygulanan kuralları altında yorumlanacağını dize değerleri olarak ilk XAML düğümü akışı depolanırlar. Anlamı bir XAML adı ve anlamı XAML türü hizalama veya yalnızca geçerli uygulama bağlı olarak bir yedekleme türü sistemde olabilir.  
  
 Pratik kullanımını desteklemek üzere `x:Members` üyeleri üye tanımları işaretlemede belirtmek için bir yol değiştirilebilir bir sınıf ile ilişkili olması gerekir. Hedeflenen modeli olan `x:Members` belirten bir tür üyesi olarak mevcut bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturmayı mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor. Bu, XAML üyesi tanımları desteği uygulama modellerini sahip tek çerçeveleri için bırakılır. Genellikle, isteğe bağlı olarak, XAML ve aşağıdakilerden birini işaretleme-derleme MSBUILD yapı eylemleri arka plan kod ile tümleştirin veya üretim saf gelen XAML derlemeleri, bu özelliği desteklemek için gereklidir.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Property` tamamen XAML veya XAML oluşan özel bir etkinlik üyelerini tanımlayan – dinamik üyeler bir etkinlik Tasarımcısı ile arka plan kod için tanımlanır. `x:Class` XAML üretim kök öğe üzerinde de belirtilmelidir. Bu, .NET Framework XAML hizmetlerinde düzeyinde bir gereksinim değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklendiğinde bir gereksinim haline gelir. Windows Workflow Foundation kullanmayan saf XAML tür adı için hedeflenen değeri olarak `x:Property` `Type` özniteliği ve bunun yerine burada belgelenmemiş bir kuralı kullanır. Daha fazla bilgi için [DynamicActivity oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd807392(v=vs.100)).
