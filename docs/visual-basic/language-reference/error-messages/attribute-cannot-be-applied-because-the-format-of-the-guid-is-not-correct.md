---
title: "'<attribute>' GUID'sinin biçimi doğru olmadığından <number>' uygulanamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: d27c326b6a88271ba4abf0144e71027f6671b17e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330681"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<özniteliği >' uygulanamaz GUID'sinin biçimi '\<sayı >' doğru değil
A `COMClassAttribute` özniteliği bloğu için bir GUID doğru biçime uygun değil bir genel benzersiz tanıtıcısı (GUID) belirtir. `COMClassAttribute` GUID'ler, sınıf, arabirim ve oluşturma olayı benzersiz şekilde tanımlamak için kullanır.  
  
 Bir GUID, 16, ilk sekiz sayısal ve ikili son sekiz bayt oluşur. Uuidgen.exe gibi Microsoft yardımcı programları tarafından oluşturulan ve alan ve zaman içinde benzersiz olması garanti edilir.  
  
 **Hata Kimliği:** BC32500  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Doğru GUID veya COM nesnesi tanımlamak gerekli GUID'leri belirleyin.  
  
2. GUID dizeleri için sunulan olun `COMClassAttribute` öznitelik bloğuna doğru kopyalanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Guid>
- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
