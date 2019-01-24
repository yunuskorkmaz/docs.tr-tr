---
title: 'Azaltma: WPF düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d75911c2087370cb9313c6694ce2630b80e635a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686042"
---
# <a name="mitigation-wpf-layout"></a>Azaltma: WPF düzeni
WPF denetimleri düzenini biraz değiştirebilirsiniz.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin ardından:  
  
-   Öğelerin yükseklik ve genişlik büyütür veya en fazla bir piksel küçültür.  
  
-   Bir nesne yerleşimini en fazla bir piksel taşıyabilirsiniz.  
  
-   Ortalanmış öğeleri yatay veya dikey olarak en fazla bir piksel merkezin olabilir.  
  
 Bu yeni bir düzen, varsayılan olarak, yalnızca .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.  
  
## <a name="mitigation"></a>Azaltma  
 Bu yana sağında veya altında yüksek Dpı'larda WPF denetimleri, kırpma ortadan kaldırmak için bu değişikliği eğilimi gösterir, ancak .NET Framework 4.6 üzerinde çalışan .NET Framework'ün önceki sürümlerini hedefleyen uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz `<runtime>` app.config dosyasının:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4.6 hedef ancak önceki yerleşimi algoritmasını kullanarak işlemek için WPF denetimleri isteyen uygulamalar bunu aşağıdaki satırı ekleyerek `<runtime>` app.config dosyasının:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
