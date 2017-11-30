---
title: "Nesne veya sınıf olay kümesini desteklemiyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Nesne veya sınıf olay kümesini desteklemiyor
Kullanmaya çalıştığınız bir `WithEvents` olayları belirtilen kümesi için bir olay kaynağı olarak çalışamaz bir bileşeni ile değişken. Örneğin, bir nesne olaylar indirilir, sonra başka bir nesne oluşturmak istediğiniz `Implements` ilk nesne. Uygulanan nesneden olayları havuzu düşünebilirsiniz karşın, bu her zaman durumda değil. `Implements`yalnızca yöntemleri ve özellikleri için bir arabirimi uygular. `WithEvents`Özel için desteklenmeyen `UserControls`, type Info yükseltmek gereken `ObjectEvent` çalışma zamanında kullanılabilir değil.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Olay kaynağı olmayan bir bileşen için olayları kapatamıyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
