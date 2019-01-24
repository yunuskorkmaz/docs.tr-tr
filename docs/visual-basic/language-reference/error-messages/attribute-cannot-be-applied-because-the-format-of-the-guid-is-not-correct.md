---
title: "&#39;&lt;öznitelik&gt; &#39; uygulanamaz GUID'sinin biçimi &#39; &lt;numarası&gt; &#39; doğru değil"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 85b8c9dcccbb307d8a744e33a5f1d4b1775fda04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623671"
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;öznitelik&gt; &#39; uygulanamaz GUID'sinin biçimi &#39; &lt;numarası&gt; &#39; doğru değil
A `COMClassAttribute` özniteliği bloğu için bir GUID doğru biçime uygun değil bir genel benzersiz tanıtıcısı (GUID) belirtir. `COMClassAttribute` GUID'ler, sınıf, arabirim ve oluşturma olayı benzersiz şekilde tanımlamak için kullanır.  
  
 Bir GUID, 16, ilk sekiz sayısal ve ikili son sekiz bayt oluşur. Uuidgen.exe gibi Microsoft yardımcı programları tarafından oluşturulan ve alan ve zaman içinde benzersiz olması garanti edilir.  
  
 **Hata Kimliği:** BC32500  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Doğru GUID veya COM nesnesi tanımlamak gerekli GUID'leri belirleyin.  
  
2.  GUID dizeleri için sunulan olun `COMClassAttribute` öznitelik bloğuna doğru kopyalanır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Guid>
- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)

