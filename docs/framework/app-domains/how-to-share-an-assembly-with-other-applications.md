---
title: 'Nasıl yapılır: bir derlemeyi diğer uygulamalarla paylaşma'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644287"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Nasıl yapılır: bir derlemeyi diğer uygulamalarla paylaşma
Derlemeler özel veya paylaşılan olabilir: varsayılan olarak, çoğu basit program özel bir derlemeden oluşur çünkü bunlar diğer uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.  

Bir derlemeyi diğer uygulamalarla paylaşmak için, [genel derleme önbelleği 'ne (GAC)](gac.md)yerleştirilmesi gerekir.  
  
Bir derlemeyi paylaşmak için:
  
1. Derlemenizi oluşturun. Daha fazla bilgi için bkz. [derlemeler oluşturma](../../standard/assembly/create.md).  
  
2. Derlemenize tanımlayıcı bir ad atayın. Daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](../../standard/assembly/sign-strong-name.md).  
  
3. Derlemenizin sürüm bilgilerini atayın. Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).  
  
4. Derlemenizi genel derleme önbelleğine ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yüklemek](install-assembly-into-gac.md).  
  
5. Diğer uygulamalardan derlemede bulunan türlere erişin. Daha fazla bilgi için bkz. [nasıl yapılır: tanımlayıcı adlı bir derlemeye başvurma](../../standard/assembly/reference-strong-named.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../../../api/index.md)
- [Programlama kavramları (Visual Basic)](../../../api/index.md)
- [Derlemeler ile programlama](../../standard/assembly/index.md)
