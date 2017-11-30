---
title: "Azaltma: WPF Düzeni"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3ba5ac792169cc076f9621025f35444281cec6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-wpf-layout"></a>Azaltma: WPF Düzeni
WPF denetimleri düzenini biraz değiştirebilirsiniz.  
  
## <a name="impact"></a>Etki  
 Bu değişikliğin sonucu olarak:  
  
-   Genişlik veya yüksekliğinden öğelerinin büyütür veya en çok bir piksel küçültür.  
  
-   Bir nesne yerleşimini en çok bir piksel taşıyabilirsiniz.  
  
-   Ortalanmış öğeleri dikey veya yatay olarak merkezi en çok bir piksel tarafından devre dışı olabilir.  
  
 Varsayılan olarak, bu yeni düzen .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.  
  
## <a name="mitigation"></a>Azaltma  
 Kırpma sağa ya da yüksek DPIs WPF denetimleri alt ortadan kaldırmak için bu değişiklik eğilimlidir olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ama .NET Framework 4.6 üzerinde çalışan uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz `<runtime>` app.config dosyasının:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 .NET Framework 4.6 hedef ancak WPF denetimleri önceki düzeni algoritmasını kullanarak oluşturmak istediğiniz uygulamalar yapabilirsiniz aşağıdaki satırı ekleyerek `<runtime>` app.config dosyasının:  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
