---
title: x:Members Yönergesi
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: 2c273fce1f15d9a5af72bc3f5a530d3c26dfc77e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564142"
---
# <a name="xmembers-directive"></a>x:Members Yönergesi
X: Class için üst öğenin uygulamak biçimlendirme içinde tanımlanan üyelerin kümesini içerir.  
  
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
|`className`|XAML üretim için yedekleme sınıfı ya da parçalı sınıf adıdır. Açıklamalar bakın.|  
|`oneOrMoreMembers`|Üye tanımları temsil eden bir veya daha fazla nesne öğeleri. Genellikle, bunlar `x:Property` nesne öğeleri. Açıklamalar bakın.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML hizmetlerinde uygulamasında yedekleme sınıfı veya yoktur için temel üye uygulaması `x:Members`. `x:Members` herhangi bir üye olarak bulunabilir özel XAML üyesi olduğu. XAML düğüm akış `x:Members` adlı bir üye temsil edilir `Members`, XAML dili XAML ad. Üye `Members` salt okunur bir genel listesini içeren `Member` nesneleri. Tipik biçimlendirmede tek tek üyeleri olarak belirtilen `x:Property` özelliği öğeleri. `x:Property` özellikle türlerinin özellikleri için daha kesin bir türü ve için atanamaz `x:Member`. Daha fazla bilgi için bkz: [x: Property yönergesi](../../../docs/framework/xaml-services/x-property-directive.md).  
  
 Pratik kullanımını desteklemek için `x:Members` üye tanımları biçimlendirmede belirtmek için bir yol üyeleri değiştirilebilir bir sınıf ile ilişkili olmalıdır. Hedeflenen modeli olan `x:Members` belirten bir türü bir üyesi olarak mevcut bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üyenin tanımları oluşturan mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor. Bu üye tanımları XAML destek uygulama modelleri sahip tek tek çerçeveler bırakılır. Genellikle, isteğe bağlı olarak işaretleme-XAML ve ya da derleme MSBUILD yapı eylemleri arka plan kodu ile tümleştirmek veya üretim XAML gelen saf derlemeler bu özelliği desteklemek için gereklidir.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>x: Members Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Members` tamamen XAML veya XAML oluşan özel bir aktivite üyeleri içerir – dinamik üyeler arka plan kodu ile bir etkinlik Tasarımcısı için tanımlanmış. `x:Class` XAML üretim kök öğesinin de belirtilmelidir. Bu, .NET Framework XAML hizmetlerinde düzeyinde zorunlu değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklenen bir gereksinim haline gelir. `x:Members` Biçimlendirme bildirir nesne öğesinin ilk alt öğe olmalıdır `x:Class`.
