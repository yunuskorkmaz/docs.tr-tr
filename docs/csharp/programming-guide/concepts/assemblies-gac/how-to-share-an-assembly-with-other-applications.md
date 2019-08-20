---
title: 'Nasıl yapılır: Bir derlemeyi diğer uygulamalarla paylaşma (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595737"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Nasıl yapılır: Bir derlemeyi diğer uygulamalarla paylaşma (C#)
Derlemeler özel veya paylaşılan olabilir: varsayılan olarak, çoğu basit program özel bir derlemeden oluşur çünkü bunlar diğer uygulamalar tarafından kullanılmak üzere tasarlanmamıştır.  
  
 Bir derlemeyi diğer uygulamalarla paylaşmak için, [genel derleme önbelleği](../../../../framework/app-domains/gac.md) 'ne (GAC) yerleştirilmesi gerekir.  
  
### <a name="sharing-an-assembly"></a>Bir derlemeyi paylaşma  
  
1. Derlemenizi oluşturun. Daha fazla bilgi için bkz. [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).  
  
2. Derlemenize tanımlayıcı bir ad atayın. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi güçlü bir adla](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)imzalayın.  
  
3. Derlemenizin sürüm bilgilerini atayın. Daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../../../framework/app-domains/assembly-versioning.md).  
  
4. Derlemenizi genel derleme önbelleğine ekleyin. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)yükler.  
  
5. Diğer uygulamalardan derlemede bulunan türlere erişin. Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı bir derlemeye](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)başvuru yapın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../index.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)
