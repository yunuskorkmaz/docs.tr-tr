---
title: 'Azaltma: WPF Düzeni'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a9bc9e14621b22cad6491f6f5132ef302e7ef06
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387344"
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
 [Yeniden Hedefleme Değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
