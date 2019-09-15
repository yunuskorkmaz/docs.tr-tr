---
title: 'Nasıl yapılır: Bir derlemeyi diğer uygulamalarla paylaşma'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972951"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>Nasıl yapılır: Bir derlemeyi diğer uygulamalarla paylaşma
Derlemeler özel veya paylaşılan olabilir: varsayılan olarak, çoğu basit program özel bir derlemeden oluşur çünkü bunlar diğer uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.  

Bir derlemeyi diğer uygulamalarla paylaşmak için, [genel derleme önbelleği 'ne (GAC)](gac.md)yerleştirilmesi gerekir.  
  
Bir derlemeyi paylaşmak için:
  
1. Derlemenizi oluşturun. Daha fazla bilgi için bkz. [derlemeler oluşturma](../../standard/assembly/create.md).  
  
2. Derlemenize tanımlayıcı bir ad atayın. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi güçlü bir adla](../../standard/assembly/sign-strong-name.md)imzalayın.  
  
3. Derlemenizin sürüm bilgilerini atayın. Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).  
  
4. Derlemenizi genel derleme önbelleğine ekleyin. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine](install-assembly-into-gac.md)yükler.  
  
5. Diğer uygulamalardan derlemede bulunan türlere erişin. Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı bir derlemeye](../../standard/assembly/reference-strong-named.md)başvuru yapın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../../../api/index.md)
- [Programlama kavramları (Visual Basic)](../../../api/index.md)
- [Bütünleştirilmiş kod içeren program](../../standard/assembly/program.md)
