---
title: Türü değeri &#39; &lt;typename1&gt; &#39; dönüştürülemez &#39; &lt;typename2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc30955
- bc30955
helpviewer_keywords:
- BC30955
ms.assetid: 966b61eb-441e-48b0-bedf-ca95384ecb8b
ms.openlocfilehash: 00ce143eecefbdf2f1b9e204ae2005be4bb81e39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627609"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39"></a>Türü değeri &#39; &lt;typename1&gt; &#39; dönüştürülemez &#39; &lt;typename2&gt;&#39;
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

