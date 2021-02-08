---
description: "Hakkında daha fazla bilgi edinin: BC30148: Bu ' Sub New ' öğesinin Ilk ifadesinin ' MyBase. New ' veya ' MyClass. New ' çağrısı olması gerekir (hiçbir parametre olmadan erişilebilir yapıcı yok)"
title: Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır (Parametreler Olmadan Erişilebilir Yapıcı Yok)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 4138055f3634c060c7416947966b1cf18fb03b94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796229"
---
# <a name="bc30148-first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a>BC30148: Bu ' Sub New ' öğesinin Ilk ifadesinin ' MyBase. New ' veya ' MyClass. New ' çağrısı olması gerekir (parametresiz erişilebilir Oluşturucu yok)

' ' Öğesinin ' ' temel sınıfında \<basename> \<derivedname> bağımsız değişken olmadan çağrılabilecek erişilebilir bir ' Sub New ' olmadığından, bu ' Sub New ' öğesinin ilk Ifadesinin ' MyBase. New ' veya ' MyClass. New ' çağrısı olması gerekir.

 Türetilmiş bir sınıfta, her oluşturucunun bir temel sınıf Oluşturucusu () çağırması gerekir `MyBase.New` . Temel sınıfta, türetilmiş sınıfların erişebileceği parametre içermeyen bir Oluşturucu varsa, `MyBase.New` otomatik olarak çağrılabilir. Aksi takdirde, bir temel sınıf oluşturucusunun parametrelerle çağrılması gerekir ve bu otomatik olarak gerçekleştirilemez. Bu durumda, her türetilmiş sınıf oluşturucusunun ilk ifadesinin temel sınıfta parametreli bir Oluşturucu çağırması veya bir temel sınıf Oluşturucu çağrısını yapan türetilmiş sınıfta başka bir Oluşturucu çağırması gerekir.

 **Hata kimliği:** BC30148

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Gerekli parametreleri çağırma ya da `MyBase.New` böyle bir çağrı yapan bir eşdüzey Oluşturucu çağırma.

     Örneğin, temel sınıfın olarak belirtilen bir Oluşturucusu varsa `Public Sub New(ByVal index as Integer)` , türetilen sınıf oluşturucusunda ilk ifade olabilir `MyBase.New(100)` .

## <a name="see-also"></a>Ayrıca bkz.

- [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
