---
title: "Yordam Aşırı Yüklemesi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65fd5a6763752c616f13891bfa5acabff6115d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-overloading-visual-basic"></a>Yordam Aşırı Yüklemesi (Visual Basic)
*Aşırı yükleme* bir yordam, aynı adlı ancak farklı parametre listeleri kullanarak birden çok sürümlerde tanımlama anlamına gelir. Aşırı yükleme amacı, ada göre ayırt zorunda kalmadan bir yordamın birden fazla yakından ilgili sürümünü tanımlamaktır. Parametre listesi değiştirerek bunu yapabilirsiniz.  
  
## <a name="overloading-rules"></a>Kuralları aşırı yüklemesi  
 Bir yordamı aşırı yükleme oluştuğunda aşağıdaki kurallar geçerli olur:  
  
-   **Aynı ada**. Aşırı yüklenmiş her sürümü aynı yordam adı kullanmanız gerekir.  
  
-   **Farklı imza**. Aşırı yüklenmiş her sürümü diğer aşırı yüklenmiş sürümleri aşağıdaki bakımlardan en az birinde farklı gerekir:  
  
    -   Parametre sayısı  
  
    -   Parametreler sırası  
  
    -   Parametre veri türleri  
  
    -   Tür parametreleri (için genel bir yordam) sayısı  
  
    -   Dönüş türü (yalnızca için bir dönüşüm işleci)  
  
     Yordam adı ile birlikte önceki öğeler toplu olarak adlandırılır *imza* yordamın. Aşırı yüklenmiş bir yordamı çağırdığınızda derleyici imza çağrı düzgün tanımını eşleşip eşleşmediğini kontrol için kullanır.  
  
-   **İmza parçası olmayan öğeler**. İmza değişen olmadan bir yordamı aşırı yükleme yapılamıyor. Özellikle, yalnızca bir veya daha fazla aşağıdaki öğelerden birini değiştirerek bir yordamı aşırı olamaz:  
  
    -   Yordam değiştiricisi anahtar sözcükler gibi `Public`, `Shared`, ve`Static`  
  
    -   Parametresi veya parametre adlarını yazın  
  
    -   Tür parametresi kısıtlamaları (için genel bir yordam)  
  
    -   Parametresi değiştiricisi anahtar sözcükler gibi `ByRef` ve`Optional`  
  
    -   Olup bir değer döndürür  
  
    -   Dönüş değeri (dışında bir dönüşüm işleci) veri türü  
  
     Önceki listedeki öğeler imza parçası değildir. Aşırı yüklenmiş sürümler arasında ayırt etmek için kullanamazsınız rağmen düzgün şekilde kendi imzaları göre ayırt edilen aşırı yüklenmiş sürümleri arasında farklılık gösterebilir.  
  
-   **Geç bağlama bağımsız değişkenleri**. Geç bağlama nesne değişkeni aşırı yüklenmiş bir sürüme geçirmek istiyorsanız, uygun parametre olarak bildirilmelidir <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Bir yordamın birden fazla sürümünü  
 Yazmakta olduğunuz varsayalım bir `Sub` adıyla veya hesap numarası müşteriye başvurabileceğiniz istediğiniz bir müşterinin bakiyesini ve karşı bir işlem sonrası için yordamı. Bunu yapabilmek için iki farklı tanımlayabilirsiniz `Sub` aşağıdaki örnekteki gibi yordamlar:  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a>Aşırı yüklenmiş sürümleri  
 Tek bir yordam adı aşırı yüklemeyi alternatiftir. Kullanabileceğiniz [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) anahtar bir sürümünü yordamı her parametre listesi için aşağıdaki gibi tanımlayın:  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a>Ek aşırı yüklemeleri  
 Ayrıca bir işlem tutarı ya da kabul etmek istiyorsanız `Decimal` veya `Single`, daha fazla aşırı `post` bu değişim için izin vermek için. Bu olmanızın her bir önceki örnekte aşırı yüklemeleri için dört olurdu `Sub` yordamları, aynı ada sahip tüm ancak dört farklı imzalar.  
  
## <a name="advantages-of-overloading"></a>Aşırı yükleme avantajları  
 Bir yordamı aşırı yükleme avantajı çağrının esneklik olmasıdır. Kullanmak için `post` yordamı çağıran kodu olarak ya da müşteri kimliği elde edebilirsiniz önceki örnekte bildirilen bir `String` veya bir `Integer`ve ardından her iki durumda da aynı yordamı çağırın. Aşağıdaki örnekte bu gösterilmektedir:  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Nasıl yapılır: bir yordamın birden fazla sürümünü tanımlama](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Nasıl yapılır: aşırı yüklenmiş bir yordamı çağırma](./how-to-call-an-overloaded-procedure.md)  
 [Nasıl yapılır: isteğe bağlı parametreler isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Nasıl yapılır: belirsiz sayıda parametre isteyen bir yordamı aşırı yükleme](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Yordamları aşırı yüklemeye ilişkin düşünceler](./considerations-in-overloading-procedures.md)  
 [Aşırı yükleme çözümü](./overload-resolution.md)  
 [Aşırı yüklemeler](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
