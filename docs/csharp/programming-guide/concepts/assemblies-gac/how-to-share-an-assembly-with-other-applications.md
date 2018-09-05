---
title: 'Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 413eb5e021c782db05abd454ebfa4e7cb1a1abcb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512914"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma
Özel veya paylaşılan derlemeler olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılmak üzere amaçlanmamıştır çünkü basit programlarının çoğu özel bir derleme oluşur.  
  
 Bir derlemeyi başka uygulamalarla paylaşma için bunu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Derlemeyi paylaşmanız  
  
1.  Derlemenizi oluşturun. Daha fazla bilgi için [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Bir derlemeye güçlü bir ad atayın. Daha fazla bilgi için [nasıl yapılır: bir derlemeyi tanımlayıcı bir adla imzalamak](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Sürüm bilgileri için bir derleme atayın. Daha fazla bilgi için [derleme sürümlendirme](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4.  Derlemenizi, Genel Derleme Önbelleği'ne ekleyin. Daha fazla bilgi için [nasıl yapılır: bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Diğer uygulamalardan derlemesinde bulunan türleri erişin. Daha fazla bilgi için [nasıl yapılır: bir Strong-Named derleme başvurusu](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
- [Bütünleştirilmiş Kodlarla Programlama](../../../../framework/app-domains/programming-with-assemblies.md)
