---
title: 'Azaltma: WPF Düzeni'
description: WPF denetimleri düzeninde, bir pikselin hareket eden bir nesnenin yerleşimi gibi bir değişikliğin sonucu olan sorunları nasıl azaltacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: caed758f6e86a1e2bee255c2f29ca3160b327e17
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244086"
---
# <a name="mitigation-wpf-layout"></a>Azaltma: WPF Düzeni

WPF denetimlerinin düzeni biraz değişebilir.  
  
## <a name="impact"></a>Etki  

 Bu değişikliğin sonucu olarak:  
  
- Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.  
  
- Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.  
  
- Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.  
  
 Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.  
  
## <a name="mitigation"></a>Risk azaltma  

 Bu değişiklik, yüksek DPA 'daki WPF denetimlerinin sağ veya alt bölümünün kırpılmasını ortadan kaldırmaya eğiliminden, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu yeni davranışı kabul edebilir `<runtime>` :  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek yapabilir  `<runtime>` :  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
