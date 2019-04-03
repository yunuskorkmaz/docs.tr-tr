---
title: "'<typename1>' türünün değeri '<typename2>' olarak dönüştürülemez (Birden fazla dosya başvurusu)"
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 58b334eb5e6db443bcfaba72729d59cb1d798e70
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833535"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >' (birden fazla dosya başvurusu)
Türünün değeri '\<typename1 >' olarak değiştirilemez '\<typename2 >'. Bir dosya başvurusu karışması tür uyuşmazlığı olabilir '\<filepath1 >' projesindeki '\<projectname1 >' için bir dosya başvurusu ile '\<filepath2 >' projesindeki '\<projectname2 >'. İki derleme de aynıysa, bu başvuruları her iki başvuru aynı konumdan olacak şekilde değiştirmeyi deneyin.  
  
 Burada bir derlemeyi birden fazla dosya başvurusu bir proje yapar bir durumda, derleyici bir türden diğerine dönüştürülüp dönüştürülemeyeceği garanti edemez.  
  
 Her dosya başvurusu bir dosya yolu ve adı (genellikle bir DLL dosyası) projenin çıkış dosyasını belirtir. Derleyici çıktı dosyaları aynı kaynaktan gelen veya aynı bütünleştirilmiş kodun aynı sürümü temsil ettiğini garanti edemez. Bu nedenle, farklı başvuruları türleri aynı türdeyse veya hatta bir diğerine dönüştürülebilir belirleyemezsiniz.  
  
 Başvurulan derlemeler aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvurusu kullanabilirsiniz. *Derleme kimliği* derlemenin adı, sürümü, ortak anahtar varsa ve kültür içerir. Bu bilgiler derlemenin benzersiz olarak tanımlar.  
  
 **Hata Kimliği:** BC30961  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Başvurulan derlemeler aynı derleme kimliği varsa, kaldırın veya yalnızca tek bir dosya başvurusu yani dosya başvurulardan birini değiştirin.  
  
-   Başvurulan derlemeler aynı derleme kimliği yoksa, diğer bir tür için tür dönüştürme denemez sonra kodunuzu değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
