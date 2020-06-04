---
title: "'<attribute>' GUID'sinin biçimi doğru olmadığından <number>' uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 554c38c8f44999feba4cfa04d58ce2f07e955eb1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409926"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<attribute>' GUID'sinin biçimi doğru olmadığından \<number>' uygulanamaz

`COMClassAttribute`Öznitelik bloğu, GUID için doğru biçime uymayan bir genel benzersiz tanımlayıcı (GUID) belirtir. `COMClassAttribute`sınıfı, arabirimi ve oluşturma olayını benzersiz şekilde tanımlamak için GUID 'Leri kullanır.  
  
 Bir GUID 16 bayttan oluşur; Bu, ilk sekiz ' un sayısal olduğu ve son sekiz ikilik bir değer. Uuidgen. exe gibi Microsoft yardımcı programları tarafından oluşturulur ve alan ve saat içinde benzersiz olarak garanti edilir.  
  
 **Hata kimliği:** BC32500  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. COM nesnesini tanımlamak için gereken doğru GUID veya GUID 'Leri belirler.  
  
2. Öznitelik bloğuna sunulan GUID dizelerinin `COMClassAttribute` doğru şekilde kopyalandığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Guid>
- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
