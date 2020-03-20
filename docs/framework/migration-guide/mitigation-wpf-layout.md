---
title: 'Azaltma: WPF Düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457788"
---
# <a name="mitigation-wpf-layout"></a>Azaltma: WPF Düzeni
WPF denetimlerinin düzeni biraz değişebilir.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin bir sonucu olarak:  
  
- Öğelerin genişliği veya yüksekliği en fazla bir piksel büyüyebilir veya küçülebilir.  
  
- Bir nesnenin yerleşimi en fazla bir piksel tarafından hareket edebilir.  
  
- Ortalanmış öğeler en fazla bir piksel ile dikey veya yatay kapalı merkezi olabilir.  
  
 Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4.6'yı hedefleyen uygulamalar için etkinleştirilir.  
  
## <a name="mitigation"></a>Risk azaltma  
 Bu değişiklik yüksek DPI'larda WPF denetimlerinin sağ veya alt kesiminin kırpma sını ortadan kaldırma eğiliminde olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET `<runtime>` Framework 4.6 üzerinde çalışan uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu yeni davranışı seçebilir:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4.6'yı hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini `<runtime>` isteyen uygulamalar, app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
