---
title: "'<attribute>' GUID'sinin biçimi doğru olmadığından <number>' uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: f7b6e42480075666ce9f7e8fc6966bd4bb6b888a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977310"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<Number > ' GUID 'sinin biçimi doğru olmadığından '\<özniteliği > ' uygulanamıyor

`COMClassAttribute` öznitelik bloğu, GUID için doğru biçime uymayan bir genel benzersiz tanımlayıcı (GUID) belirtir. `COMClassAttribute` sınıfı, arabirimi ve oluşturma olayını benzersiz şekilde tanımlamak için GUID 'Leri kullanır.  
  
 Bir GUID 16 bayttan oluşur; Bu, ilk sekiz ' un sayısal olduğu ve son sekiz ikilik bir değer. Uuidgen. exe gibi Microsoft yardımcı programları tarafından oluşturulur ve alan ve saat içinde benzersiz olarak garanti edilir.  
  
 **Hata kimliği:** BC32500  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. COM nesnesini tanımlamak için gereken doğru GUID veya GUID 'Leri belirler.  
  
2. `COMClassAttribute` Attribute bloğuna sunulan GUID dizelerinin doğru şekilde kopyalandığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Guid>
- [Özniteliklere genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
