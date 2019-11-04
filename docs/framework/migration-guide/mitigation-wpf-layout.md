---
title: 'Azaltma: WPF Düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457788"
---
# <a name="mitigation-wpf-layout"></a>Azaltma: WPF Düzeni
WPF denetimlerinin düzeni biraz değişebilir.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin sonucu olarak:  
  
- Öğelerin genişliği veya yüksekliği, en fazla bir piksel ile büyüyebilir veya küçülebilir.  
  
- Bir nesnenin yerleştirilmesi en çok bir piksel kadar hareket edebilir.  
  
- Ortalanmış öğeler, en fazla bir piksel olarak orta veya yatay olarak devre dışı olabilir.  
  
 Varsayılan olarak, bu yeni düzen yalnızca .NET Framework 4,6 ' i hedefleyen uygulamalar için etkindir.  
  
## <a name="mitigation"></a>Azaltma  
 Bu değişiklik, yüksek DPG 'de WPF denetimlerinin sağ veya alt kısmının kırpılmasını ortadan kaldıran eğilimi yaptığından, .NET Framework önceki sürümlerini hedefleyen ancak .NET Framework 4,6 üzerinde çalışan uygulamalar, @no aşağıdaki satırı ekleyerek bu yeni davranışı kabul edebilir App. config dosyasının __t_0_ bölümü:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4,6 ' i hedefleyen ancak WPF denetimlerinin önceki düzen algoritmasını kullanarak işlemesini tercih eden uygulamalar, App. config dosyasının `<runtime>` bölümüne aşağıdaki satırı ekleyerek bunu yapabilir:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama uyumluluğu](application-compatibility.md)
