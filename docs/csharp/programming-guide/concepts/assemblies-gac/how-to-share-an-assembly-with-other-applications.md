---
title: 'Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: a5b20061c759fd914193f24aa123317f13d31dce
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866471"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma
Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.  
  
 Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Derlemeyi paylaşmanız  
  
1.  Derlemenizi oluşturun. Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Bir derlemeye güçlü bir ad atayın. Daha fazla bilgi için [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Sürüm bilgileri için bir derleme atayın. Daha fazla bilgi için [derleme sürümlendirme](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4.  Derlemenizi, Genel Derleme Önbelleği'ne ekleyin. Daha fazla bilgi için [nasıl yapılır: bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Diğer uygulamalardan derlemesinde bulunan türleri erişin. Daha fazla bilgi için [nasıl yapılır: bir Strong-Named derleme başvurusu](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)
