---
title: x:Members Yönergesi
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: d23e6b459af932e0a6f69309f26a1cce70a9d256
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938898"
---
# <a name="xmembers-directive"></a>x:Members Yönergesi
X: sınıf için üst öğenin geçerli biçimlendirme içinde tanımlanan üyelerin kümesini tutar.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`className`|XAML üretim için yedekleme sınıf veya kısmi sınıf adıdır. Açıklamalara bakın.|  
|`oneOrMoreMembers`|Üye tanımları temsil eden bir veya daha fazla nesne öğeleri. Bunlar genellikle `x:Property` nesne öğeleri. Açıklamalara bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML hizmetlerinde uygulama, yedekleme sınıfı veya yoktur için temel alınan üye uygulama `x:Members`. `x:Members` herhangi bir üyesi olarak bulunabilir özel bir XAML üye var. XAML düğüm akış `x:Members` adlı bir üyesi olarak temsil edilen `Members`, XAML dili XAML ad uzayındaki. Üye `Members` salt okunur bir genel listesini içeren `Member` nesneleri. Tipik biçimlendirme içinde tek tek üyeleri olarak belirtilen `x:Property` özellik öğeleri. `x:Property` özellikle türlerin özellikleri için daha kesin bir tür ve öğesine atanamaz `x:Member`. Daha fazla bilgi için [x: Property yönergesi](x-property-directive.md).  
  
 Pratik kullanımını desteklemek üzere `x:Members` üyeleri üye tanımları işaretlemede belirtmek için bir yol değiştirilebilir bir sınıf ile ilişkili olması gerekir. Hedeflenen modeli olan `x:Members` belirten bir tür üyesi olarak mevcut bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üye tanımları oluşturmayı mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor. Bu, XAML üyesi tanımları desteği uygulama modellerini sahip tek çerçeveleri için bırakılır. Genellikle, isteğe bağlı olarak, XAML ve aşağıdakilerden birini işaretleme-derleme MSBUILD yapı eylemleri arka plan kod ile tümleştirin veya üretim saf gelen XAML derlemeleri, bu özelliği desteklemek için gereklidir.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Members` tamamen XAML veya XAML oluşan özel bir etkinlik üyelerini içeren – dinamik üyeler bir etkinlik Tasarımcısı ile arka plan kod için tanımlanır. `x:Class` XAML üretim kök öğe üzerinde de belirtilmelidir. Bu, .NET Framework XAML hizmetlerinde düzeyinde bir gereksinim değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklendiğinde bir gereksinim haline gelir. `x:Members` ilk biçimlendirme bildirir nesne öğesinin alt öğesi olmalıdır `x:Class`.
