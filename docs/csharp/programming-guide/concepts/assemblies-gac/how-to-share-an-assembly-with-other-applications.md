---
title: "Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dedbd90cdc6f33bfa03ce5e38138ca3b23178b95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Nasıl yapılır: bir derlemeyi başka uygulamalarla (C#) paylaşma
Derlemeler, özel veya paylaşılan olabilir: varsayılan olarak, diğer uygulamalar tarafından kullanılması amaçlanmıştır değil çünkü basit programlarının çoğu özel bir derlemenin oluşur.  
  
 Bir derlemeyi başka uygulamalarla paylaşma için onu yerleştirilmelidir [genel derleme önbelleği](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Bir derlemeyi paylaşımı  
  
1.  Derlemenizi oluşturun. Daha fazla bilgi için bkz: [derlemeler oluşturma](../../../../framework/app-domains/create-assemblies.md).  
  
2.  Güçlü bir ad, derlemenizi atayın. Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi tanımlayıcı adla oturum](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3.  Sürüm bilgileri, derlemenizi atayın. Daha fazla bilgi için bkz: [derleme sürümü oluşturma](https://msdn.microsoft.com/library/51ket42z).  
  
4.  Derleme genel derleme önbelleğine ekleme. Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5.  Diğer uygulamalardan derlemesinde bulunan türleri erişin. Daha fazla bilgi için bkz: [nasıl yapılır: bir Strong-Named derleme başvurusu](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Derlemelerle programlama](../../../../framework/app-domains/programming-with-assemblies.md)
