---
title: "'<typename1>' türünün değeri '<typename2>' olarak değiştirilemez"
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 67cb8ac602437474f35c89c9aecf66fbf40c91c9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875042"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2"></a>'\<typename1>' türünün değeri '\<typename2>' olarak değiştirilemez

' ' Türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> . Tür uyumsuzluğu, ' ' derlemesine bir proje başvurusuyla bir dosya başvurusunun karıştırılması nedeniyle olabilir \<assemblyname> . ' ' Projesindeki ' ' adlı dosya başvurusunu ' ' \<filepath> \<projectname1> için bir proje başvurusuyla değiştirmeyi deneyin \<projectname2> .  
  
 Bir projenin hem bir proje başvurusu hem de bir dosya başvurusu yaptığı durumlarda, derleyici bir türün diğerine dönüştürülebileceğini garanti edemez.  
  
 Aşağıdaki sözde kod, bu hatayı oluşturabilecek bir durumu gösterir.  
  
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
  
 Project `P1` , proje aracılığıyla dolaylı bir proje başvurusunu `P2` `P3` ve ayrıca öğesine doğrudan bir dosya başvurusu yapar `P3` . Bildirimi, için `commonObject` Dosya başvurusunu kullanır `P3` , ancak öğesine yapılan çağrı, `P2.getCommonClass` proje başvurusunu kullanır `P3` .  
  
 Bu durumda, dosya başvurusunun çıkış dosyası (genellikle p3.dll) için bir dosya yolu ve adı ve proje, proje `P3` adına göre kaynak projeyi ( `P3` ) tanımlar. Bu nedenle, derleyici türün `P3.commonClass` iki farklı başvuru aracılığıyla aynı kaynak kodundan geldiğini garanti edemez.  
  
 Bu durum genellikle proje başvuruları ve dosya başvuruları karmaysa oluşur. Önceki çizimde, `P1` `P3` bir dosya başvurusu yerine öğesine doğrudan proje başvurusu yapıldıysa sorun oluşmaz.  
  
 **Hata kimliği:** BC30955  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Dosya başvurusunu bir proje başvurusuyla değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Tür Dönüştürmeleri](../../programming-guide/language-features/data-types/type-conversions.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
