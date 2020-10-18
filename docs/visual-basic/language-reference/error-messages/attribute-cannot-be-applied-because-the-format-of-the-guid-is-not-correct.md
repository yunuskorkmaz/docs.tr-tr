---
title: "'<attribute>' GUID'sinin biçimi doğru olmadığından <number>' uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 8e9ac019470685d9fc45342273096d678a29428d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162654"
---
# <a name="bc32500-attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>' \<attribute> ' GUID 'sinin biçimi \<number> doğru OLMADıĞıNDAN, BC32500: ' ' uygulanamıyor

`COMClassAttribute`Öznitelik bloğu, GUID için doğru biçime uymayan bir genel benzersiz tanımlayıcı (GUID) belirtir. `COMClassAttribute` sınıfı, arabirimi ve oluşturma olayını benzersiz şekilde tanımlamak için GUID 'Leri kullanır.

 Bir GUID 16 bayttan oluşur; Bu, ilk sekiz ' un sayısal olduğu ve son sekiz ikilik bir değer. uuidgen.exe gibi Microsoft yardımcı programları tarafından oluşturulur ve alan ve saat içinde benzersiz olarak garanti edilir.

 **Hata kimliği:** BC32500

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. COM nesnesini tanımlamak için gereken doğru GUID veya GUID 'Leri belirler.

2. Öznitelik bloğuna sunulan GUID dizelerinin `COMClassAttribute` doğru şekilde kopyalandığından emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Guid>
- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
