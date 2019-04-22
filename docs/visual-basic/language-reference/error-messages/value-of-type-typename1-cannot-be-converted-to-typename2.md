---
title: "'<typename1>' türünün değeri '<typename2>' olarak değiştirilemez"
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 5f313a43bc3a2f983dabbd45477d120fdb80d063
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829035"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >'
Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >'. Derleme bir proje başvurusu olan bir dosya başvurusunun karışması tür uyuşmazlığı olabilir '\<assemblyname >'. Dosya başvurusu değiştirmeyi deneyin '\<DosyaYolu >' projesinde '\<projectname1 >' proje başvurusu ile '\<projectname2 >'.  
  
 Bir proje, hem bir proje başvurusu hem de bir dosya başvurusu burada yapar bir durumda, derleyici bir türden diğerine dönüştürülüp dönüştürülemeyeceği garanti edemez.  
  
 Bu hatayı oluşturan durumu aşağıdaki sözde kod gösterilmiştir.  
  
 `' ================ Visual Basic project P1 ================`  
  
 `'        P1 makes a PROJECT REFERENCE to project P2`  
  
 `'        and a FILE REFERENCE to project P3.`  
  
 `Public commonObject As P3.commonClass`  
  
 `commonObject = P2.getCommonClass()`  
  
 `' ================ Visual Basic project P2 ================`  
  
 `'        P2 makes a PROJECT REFERENCE to project P3`  
  
 `Public Function getCommonClass() As P3.commonClass`  
  
 `Return New P3.commonClass`  
  
 `End Function`  
  
 `' ================ Visual Basic project P3 ================`  
  
 `Public Class commonClass`  
  
 `End Class`  
  
 Proje `P1` bir proje aracılığıyla dolaylı proje başvuru yapar `P2` projesine `P3`ve ayrıca doğrudan bir dosya başvurusu `P3`. Bildirimi `commonObject` dosya başvurur `P3`, while çağrısı `P2.getCommonClass` proje başvurur `P3`.  
  
 Dosya başvurusu bir dosya yolu ve çıkış dosyasının adını belirtir, bu durum sorun olduğunu `P3` (genellikle p3.dll) kaynak projenin proje başvurularını tanımlamak sırada (`P3`) tarafından proje adı. Bu nedenle, derleyici bu tür garanti edemez `P3.commonClass` aynı kaynak kodunun iki farklı başvuruları ile gelir.  
  
 Bu durum genellikle ortaya başvurular'ne zaman proje ve dosya başvuruları karma. Önceki çizimde, sorun oluşmaz `P1` doğrudan proje başvurusu yapılan `P3` yerine dosya başvurusu.  
  
 **Hata Kimliği:** BC30955  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Dosya başvurusu bir proje başvurusu olarak değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
