---
ms.openlocfilehash: 9c2ee4ba66deb7c3b33698963add2b8a7e70069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803254"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Özel DataTemplates kullanırken ÖğelerDenetimleri'nde (ListBox ve DataGrid gibi) alt öğeye kaydırılamıyor

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, .NET Framework 4.5'teki bir hata, Özel <xref:System.Windows.Controls.ListBox?displayProperty=name> <xref:System.Windows.Controls.ComboBox?displayProperty=name>DataTemplates kullanırken ItemsControls'ün (örneğin, , <xref:System.Windows.Controls.DataGrid?displayProperty=name>vb.) alt öğesine kaydırılmamasına neden olur. Kaydırma ikinci kez denenmişse (yukarı kaydırdıktan sonra), daha sonra çalışır.|
|Öneri|Bu sorun .NET Framework 4.5.2'de giderilmiştir ve .NET Framework'ün bu sürümüne (veya sonraki bir sürüme) yükseltilerek giderilebilir. Alternatif olarak, kullanıcılar kaydırma çubuklarını bu koleksiyondaki son öğelere sürüklemeye devam edebilir, ancak bunu başarıyla yapmak için iki kez denemeleri gerekebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma Zamanı|
