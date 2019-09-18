---
title: x:Members Yönergesi
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053764"
---
# <a name="xmembers-directive"></a>x:Members Yönergesi
, Üst öğenin x:Class 'ı için uygulanan, biçimlendirme içinde tanımlanan bir üye kümesini tutar.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`className`|XAML üretimi için yedekleme sınıfının veya kısmi sınıfın adı. Bkz. açıklamalar.|  
|`oneOrMoreMembers`|Üye tanımlarını temsil eden bir veya daha fazla nesne öğesi. Genellikle, bunlar `x:Property` nesne öğeleridir. Bkz. açıklamalar.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML Hizmetleri uygulamasında, için `x:Members`bir destek sınıfı veya temel üye uygulama yoktur. `x:Members`, herhangi bir türde üye olarak var olan özel bir XAML üyesidir. Xaml düğüm akışında `x:Members` xaml Language xaml ad alanından adında `Members`bir üye olarak temsil edilir. Üye `Members` , `Member` nesnelerin salt okunurdur genel bir listesini içerir. Tipik biçimlendirmede, bireysel Üyeler özellik öğeleri olarak `x:Property` belirtilir. `x:Property`, özellikle türlerin özellikleri için daha kesin bir tür ve atanabilir `x:Member`. Daha fazla bilgi için bkz. [X:Property yönergesi](x-property-directive.md).  
  
 ' Nin pratik kullanımını, `x:Members` İşaretlemede üye tanımlarının belirtilmesi için bir yol olarak desteklemek amacıyla, üyelerin değiştirilebilen bir sınıfla ilişkilendirilmesi gerekir. Hedeflenen model `x:Members` , bir `x:Class`türü belirten bir üye olarak mevcuttur. Ancak, türleri ve üyeleri ilişkilendirme mekanizması veya dinamik üye tanımlarının üretilmesinin .NET Framework XAML Hizmetleri düzeyinde desteklenmez. Bu, XAML 'den üye tanımlarını destekleyen uygulama modelleri olan tek tek çerçeveler için bırakılır. Genellikle, XAML 'yi biçimlendirme-derleme ve bu özelliği desteklemeye yönelik saf from-XAML derlemeleri ile tümleştirme sağlayan MSBUILD derleme eylemleri.  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>Windows Workflow Foundation için x:Members  
 Windows Workflow Foundation için, `x:Members` tamamen XAML 'de oluşturulan özel bir etkinliğin üyelerini veya arka plan kodu içeren bir etkinlik Tasarımcısı için XAML tanımlı dinamik üyeleri içerir. `x:Class`Ayrıca XAML üretiminin kök öğesinde de belirtilmelidir. Bu, .NET Framework XAML Hizmetleri düzeyinde bir gereklilik değildir, ancak XAML üretimi özel etkinlikleri destekleyen MSBUILD derleme eylemleri tarafından yüklendiğinde ve genel olarak XAML Windows Workflow Foundation bir gereksinim haline gelir. `x:Members`' i bildiren `x:Class`nesne öğesinin işaretlemesinin ilk alt öğesi olması gerekir.
