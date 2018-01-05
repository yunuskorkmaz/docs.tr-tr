---
title: "x:Member Yönergesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d8394ef-644c-4331-b6c5-be855d392980
caps.latest.revision: "5"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ea04dfe5f3c371acbb388256b0854b0da8f45a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="xmember-directive"></a>x:Member Yönergesi
XAML üyesi biçimlendirmede bildirir.  
  
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
|`className`|XAML üretim için yedekleme sınıfı ya da parçalı sınıf adıdır.|  
|`memberName`|Tanımlanan özelliğinin üye adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework XAML hizmetlerinde uygulamasında. `x:Member`Yedekleme doğrudan türüne sahip değil, ancak tarafından desteklenen <xref:System.Windows.Markup.MemberDefinition> sınıfı. XAML düğümü akışı içinde bir `x:Member` öğesi adlı bir üye temsil edilir `Member`, XAML dili XAML ad. Üye `Member` biçimlendirme tarafından bildirilen şekilde öznitelikleri tutar.  
  
 Anlamını `Name` ve `Type` .NET Framework XAML hizmetlerinde düzeyinde atanmaz. Bunlar daha sonra belirli çerçeveleri tarafından uygulanan kuralları altında yorumlanan dize değerleri, ilk XAML düğüm akış içinde depolanır. Anlamı bir XAML ad ve XAML türü anlamı Hizala veya yalnızca uygulama bağlı olarak bir yedekleme türü sistemindeki geçerli olabilir.  
  
 Pratik kullanımını desteklemek için `x:Members` üye tanımları biçimlendirmede belirtmek için bir yol üyeleri değiştirilebilir bir sınıf ile ilişkili olmalıdır. Hedeflenen modeli olan `x:Members` belirten bir türü bir üyesi olarak mevcut bir `x:Class`. Ancak, türleri ve üyeleri ilişkilendirme veya dinamik üyenin tanımları oluşturan mekanizması .NET Framework XAML hizmetlerinde düzeyinde desteklenmiyor. Bu üye tanımları XAML destek uygulama modelleri sahip tek tek çerçeveler bırakılır. Genellikle, isteğe bağlı olarak işaretleme-XAML ve ya da derleme MSBUILD yapı eylemleri arka plan kodu ile tümleştirmek veya üretim XAML gelen saf derlemeler bu özelliği desteklemek için gereklidir.  
  
## <a name="xproperty-for-windows-workflow-foundation"></a>x: özellik Windows Workflow Foundation için  
 Windows Workflow Foundation için `x:Property` tamamen XAML veya XAML oluşan özel bir aktivite üyelerini tanımlayan – dinamik üyeler arka plan kodu ile bir etkinlik Tasarımcısı için tanımlanmış. `x:Class`XAML üretim kök öğesinin de belirtilmelidir. Bu, .NET Framework XAML hizmetlerinde düzeyinde zorunlu değildir, ancak XAML üretim özel etkinlikler ve Windows Workflow Foundation XAML genel destek MSBUILD yapı eylemleri tarafından yüklenen bir gereksinim haline gelir. Windows Workflow Foundation kullanmaz saf XAML tür adı için hedeflenen değeri olarak `x:Property` `Type` özniteliği ve bunun yerine belgelenmemiştir bir kuralı burada kullanır. Daha fazla bilgi için bkz: [dinamik etkinlik oluşturma](http://msdn.microsoft.com/library/dd807392.aspx).
