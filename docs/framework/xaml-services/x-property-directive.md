---
title: "x:Property Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 618555a8-c893-455c-810f-ac54cd24ef10
caps.latest.revision: "6"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: a59eb23ab3ed6ee6adbbebab0859caffd293b24f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
|`className`|XAML üretim için yedekleme sınıfı ya da parçalı sınıf adıdır.|  
|`propertyName`|Tanımlanan özelliğinin üye adı.|  
|`propertyType`|Tür adı (veya diğer dize form çerçeveye özel), bu özelliğin türünü belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML hizmetlerinde uygulamasında. `x:Property`Yedekleme doğrudan türüne sahip değil, ancak tarafından desteklenen <xref:System.Windows.Markup.PropertyDefinition> sınıfı. XAML düğümü akışı içinde bir `x:Property` öğesi adlı bir üye temsil edilir `Property`, XAML dili XAML ad. Üye `Property` biçimlendirme tarafından bildirilen şekilde öznitelikleri tutun.  
  
 Anlamını `Name` ve `Type` .NET Framework XAML hizmetlerinde düzeyinde atanmaz. Bunlar daha sonra belirli çerçeveleri tarafından uygulanan kuralları altında yorumlanan dize değerleri, ilk XAML düğüm akış içinde depolanır. Anlamı bir XAML ad ve XAML türü anlamı Hizala veya yalnızca uygulama bağlı olarak bir yedekleme türü sistemindeki geçerli olabilir.  
  
 Pratik kullanımını desteklemek için `x:Members` üye tanımları biçimlendirmede belirtmek için bir yol üyeleri değiştirilebilir bir sınıf ile ilişkili olmalıdır. Hedeflenen modeli olan `x:Members` belirten bir türü bir üyesi olarak mevcut bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üyenin tanımları oluşturan mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor. Bu üye tanımları XAML destek uygulama modelleri sahip tek tek çerçeveler bırakılır. Genellikle, isteğe bağlı olarak işaretleme-XAML ve ya da derleme MSBUILD yapı eylemleri arka plan kodu ile tümleştirmek veya üretim XAML gelen saf derlemeler bu özelliği desteklemek için gereklidir.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: özellik Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Property` tamamen XAML veya XAML oluşan özel bir aktivite üyelerini tanımlayan – dinamik üyeler arka plan kodu ile bir etkinlik Tasarımcısı için tanımlanmış. `x:Class`XAML üretim kök öğesinin de belirtilmelidir. Bu, .NET Framework XAML hizmetlerinde düzeyinde zorunlu değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklenen bir gereksinim haline gelir. Windows Workflow Foundation kullanmaz saf XAML tür adı için hedeflenen değeri olarak `x:Property` `Type` özniteliği ve bunun yerine belgelenmemiştir bir kuralı burada kullanır. Daha fazla bilgi için bkz: [dinamik etkinlik oluşturma](http://msdn.microsoft.com/library/dd807392.aspx).
