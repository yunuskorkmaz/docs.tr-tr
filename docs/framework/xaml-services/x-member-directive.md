---
title: x:Member Yönergesi
ms.date: 03/30/2017
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
ms.openlocfilehash: dfc08d79bd8206269807d88d2c659f13be487276
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43801573"
---
# <a name="xmember-directive"></a>x:Member Yönergesi
XAML biçimlendirmede üye bildirir.  
  
## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı  
  
```  
<object x:Class="className">  
  <x:Members>  
    <x:Member Name="propertyName"/>  
    additionalMembers  
  </x:Members>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`className`|XAML üretim için yedekleme sınıf veya kısmi sınıf adıdır.|  
|`memberName`|Tanımlanan özellik üyesinin adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML hizmetlerinde uygulamasında. `x:Member` Yedekleme doğrudan bir türün yok, ancak tarafından desteklenen <xref:System.Windows.Markup.MemberDefinition> sınıfı. XAML düğüm akış bir `x:Member` öğesi adlı bir üyesi olarak temsil edilir `Member`, XAML dili XAML ad uzayındaki. Üye `Member` biçimlendirme tarafından bildirilen gibi öznitelikleri içerir.  
  
 Anlamını `Name` ve `Type` .NET Framework XAML hizmetlerinde düzeyinde atanmaz. Daha sonra belirli çerçeveleri tarafından uygulanan kuralları altında yorumlanacağını dize değerleri olarak ilk XAML düğümü akışı depolanırlar. Anlamı bir XAML adı ve anlamı XAML türü hizalama veya yalnızca geçerli uygulama bağlı olarak bir yedekleme türü sistemde olabilir.  
  
 Pratik kullanımını desteklemek üzere `x:Members` üyeleri üye tanımları işaretlemede belirtmek için bir yol değiştirilebilir bir sınıf ile ilişkili olması gerekir. Hedeflenen modeli olan `x:Members` belirten bir tür üyesi olarak mevcut bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturmayı mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor. Bu, XAML üyesi tanımları desteği uygulama modellerini sahip tek çerçeveleri için bırakılır. Genellikle, isteğe bağlı olarak, XAML ve aşağıdakilerden birini işaretleme-derleme MSBUILD yapı eylemleri arka plan kod ile tümleştirin veya üretim saf gelen XAML derlemeleri, bu özelliği desteklemek için gereklidir.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: Property Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Property` tamamen XAML veya XAML oluşan özel bir etkinlik üyelerini tanımlayan – dinamik üyeler bir etkinlik Tasarımcısı ile arka plan kod için tanımlanır. `x:Class` XAML üretim kök öğe üzerinde de belirtilmelidir. Bu, .NET Framework XAML hizmetlerinde düzeyinde bir gereksinim değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklendiğinde bir gereksinim haline gelir. Windows Workflow Foundation kullanmayan saf XAML tür adı için hedeflenen değeri olarak `x:Property` `Type` özniteliği ve bunun yerine burada belgelenmemiş bir kuralı kullanır. Daha fazla bilgi için [dinamik etkinliği oluşturma](https://msdn.microsoft.com/library/dd807392.aspx).
