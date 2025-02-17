---
description: "Hakkında daha fazla bilgi edinin: BC30961: ' ' türünün değeri <typename1> ' ' olarak dönüştürülemez <typename2> (birden fazla dosya başvurusu)"
title: "'<typename1>' türünün değeri '<typename2>' olarak dönüştürülemez (Birden fazla dosya başvurusu)"
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 77f8f3c500f9f395d3998261a218175e49f0f52b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640868"
---
# <a name="bc30961-value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a>BC30961: ' ' türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> (birden fazla dosya başvurusu)

' ' Türünün değeri \<typename1> ' ' olarak dönüştürülemez \<typename2> . ' ' Projesindeki ' ' \<filepath1> \<projectname1> öğesine bir dosya başvurusu olan ' ' projesindeki ' ' öğesine bir dosya başvurusu karıştırılması nedeniyle tür uyumsuzluğu olabilir \<filepath2> \<projectname2> . Her iki derleme de aynıysa, bu başvuruları her iki başvuruyu da aynı konumdan değiştirmeyi deneyin.

 Bir projenin bir derlemeye birden fazla dosya başvurusu yaptığı durumlarda, derleyici bir türün diğerine dönüştürülebileceğini garanti edemez.

 Her dosya başvurusu, bir projenin çıkış dosyası (genellikle bir DLL dosyası) için bir dosya yolu ve adı belirtir. Derleyici, çıkış dosyalarının aynı kaynaktan gelmesini veya aynı derlemenin aynı sürümünü temsil ettiğini garanti edemez. Bu nedenle, farklı başvurularda bulunan türlerin aynı türde veya hatta diğeri diğerine dönüştürülebileceğinizin garantisi yoktur.

 Başvurulan derlemelerin aynı derleme kimliğine sahip olduğunu biliyorsanız, tek bir dosya başvurusu kullanabilirsiniz. *Derleme kimliği* , derleme adı, sürümü, varsa ortak anahtar ve kültür içerir. Bu bilgiler derlemeyi benzersiz şekilde tanımlar.

 **Hata kimliği:** BC30961

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Başvurulan derlemeler aynı derleme kimliğine sahip ise, yalnızca tek bir dosya başvurusu olacak şekilde dosya başvurularından birini kaldırın veya değiştirin.

- Başvurulan derlemeler aynı derleme kimliğine sahip değilse, bir türü birindeki bir türe dönüştürmeye çalışmayacak şekilde kodunuzu değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Tür Dönüştürmeleri](../../programming-guide/language-features/data-types/type-conversions.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
