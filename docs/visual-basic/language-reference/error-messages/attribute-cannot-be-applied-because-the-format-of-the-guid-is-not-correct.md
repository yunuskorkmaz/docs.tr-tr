---
title: '&#39;&lt;öznitelik&gt; &#39; olduğundan uygulanamıyor GUID biçimi &#39; &lt;numarası&gt; &#39; doğru değil'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 93b208b2119942f939a3af223c2f562c6097f7a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587566"
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;öznitelik&gt; &#39; olduğundan uygulanamıyor GUID biçimi &#39; &lt;numarası&gt; &#39; doğru değil
A `COMClassAttribute` özniteliği bloğu için bir GUID düzgün biçime uymuyor bir genel benzersiz tanımlayıcı (GUID) belirtir. `COMClassAttribute` sınıfı, arabirimi ve oluşturma olay benzersiz şekilde tanımlamak için GUID'leri kullanır.  
  
 Bir GUID 16 biri ilk sekiz sayısal ve son sekiz ikili bayt oluşur. Uuidgen.exe gibi Microsoft yardımcı programlar tarafından oluşturulan ve alan ve zaman içinde benzersiz olması garanti edilmez.  
  
 **Hata Kimliği:** BC32500  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Doğru GUID veya GUID'leri COM nesnesi tanımlamak gerekli belirleyin.  
  
2.  GUID dizeleri için sunulan olun `COMClassAttribute` öznitelik blok düzgün kopyalanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Guid>  
[Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)

