---
title: Mayı WPF düzeni
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d266ad33110d2bda8f7911d89981c372624c3f36
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779073"
---
# <a name="mitigation-wpf-layout"></a>Mayı WPF düzeni
WPF denetimlerinin düzeni biraz değişebilir.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin sonucu olarak:  
  
- Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.  
  
- Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.  
  
- Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.  
  
 Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik, yüksek DPG 'de WPF denetimlerinin sağ veya alt kısmının kırpılmasını ortadan kaldıran eğilimi yaptığından, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar bu yeni davranışa aşağıdaki satırı ekleyerek `<runtime>` App. config dosyasının bölümü:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, App. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Hedefleme Değişiklikleri](retargeting-changes-in-the-net-framework-4-6.md)
