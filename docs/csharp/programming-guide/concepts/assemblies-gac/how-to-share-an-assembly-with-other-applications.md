---
title: 'Nasıl yapılır: Bir derlemeyi başka uygulamalarla paylaşma (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702938"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Nasıl yapılır: Bir derlemeyi başka uygulamalarla paylaşma (C#)
Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.  
  
 Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Derlemeyi paylaşmanız  
  
1. Derlemenizi oluşturun. Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).  
  
2. Bir derlemeye güçlü bir ad atayın. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi katı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Sürüm bilgileri için bir derleme atayın. Daha fazla bilgi için [derleme sürümlendirme](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4. Derlemenizi, Genel Derleme Önbelleği'ne ekleyin. Daha fazla bilgi için [nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5. Diğer uygulamalardan derlemesinde bulunan türleri erişin. Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı bir derlemeye başvuru](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)
