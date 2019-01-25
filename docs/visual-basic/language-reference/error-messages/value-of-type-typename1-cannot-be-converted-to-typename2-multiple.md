---
title: Türü değeri &#39; &lt;typename1&gt; &#39; dönüştürülemez &#39; &lt;typename2&gt; &#39; (birden fazla dosya başvurusu)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 943b9612a9217b90c19f34285e812c4e1cccf81a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691383"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>Türü değeri &#39; &lt;typename1&gt; &#39; dönüştürülemez &#39; &lt;typename2&gt; &#39; (birden fazla dosya başvurusu)
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

