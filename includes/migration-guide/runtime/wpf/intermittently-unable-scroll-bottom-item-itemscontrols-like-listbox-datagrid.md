---
ms.openlocfilehash: 2674edc595d8e4e1e4c2ee42b39aa59265127462
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803254"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a>Aralıklı olarak oluşturulamıyor (örneğin, liste ve DataGrid) ItemsControls alt öğeye ilerlemek özel DataTemplates kullanırken

|   |   |
|---|---|
|Ayrıntılar|Bazı durumlarda, .NET Framework 4.5 hatada ItemsControls neden oluyor (gibi <xref:System.Windows.Controls.ListBox?displayProperty=name>, <xref:System.Windows.Controls.ComboBox?displayProperty=name>, <xref:System.Windows.Controls.DataGrid?displayProperty=name>, vs.) için kendi alt öğesi özel DataTemplates kullanırken kaydırma değil. Kaydırma (Yedekleme kaydırma sonra) ikinci bir kez girişiminde bulunulursa, sonra çalışır.|
|Öneri|Bu sorun, .NET Framework 4.5.2 sabit ve bu sürümü (veya sonraki bir sürümü) .NET Framework'ün yükselterek desteklenebilir. Alternatif olarak, kullanıcılar yine de bu koleksiyonlardaki son öğelerine kaydırma çubukları sürükleyebilirsiniz, ancak iki kez başarıyla Bunu yapmak denemeniz gerekebilir.|
|Kapsam|İkincil|
|Sürüm|4,5|
|Tür|Çalışma zamanı|

