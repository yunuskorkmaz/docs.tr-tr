---
title: Resume deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 853f3fe060b70c8a43957d3c843fb95539981679
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39296162"
---
# <a name="resume-statement"></a>Resume Deyimi
Bir hata işleme yordamını tamamlandıktan sonra yürütmeye devam eder.  
  
 Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Bölümler  
 `Resume`  
 Gerekli. Hata işleyicisi aynı yordam içinde hata oluştu, hataya neden olan deyim yürütmeye devam eder. Çağrılan bir yordamda hata oluştuysa, son hata işleme yordamını içeren yordam dışında adlı deyimindeki yürütmeyi devam ettirir.  
  
 `Next`  
 İsteğe bağlı. Hata işleyicisi aynı yordam içinde hata oluştu, yürütme hemen bir hataya yol açmayan deyiminin sonrasındaki deyime ile devam eder. Adlı bir yordamda hata oluştuysa, hemen en son hata işleme yordamını içeren yordam dışında çağrılan deyiminin sonrasındaki deyime ile yürütme sürdürür (veya `On Error Resume Next` deyimi).  
  
 `line`  
 İsteğe bağlı. Yürütmeye devam eder gerekli belirtilen satır `line` bağımsız değişken. `line` Bağımsız değişkeni bir satır etiket ya da satır numarasını ve hata işleyicisini aynı yordam içinde olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Kullanıyorsanız bir `Resume` deyiminde herhangi bir yere dışında bir hata işleme yordamı, bir hata oluşur.  
  
 `Resume` Deyimi içeren herhangi bir yordamda kullanılamaz bir `Try...Catch...Finally` deyimi.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Resume` hata bir yordamda işleme ve sonra da hataya neden deyimi yürütme devam deyimi. Hata numarası 55 kullanımını göstermek için oluşturulan `Resume` deyimi.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Error Deyimi](../../../visual-basic/language-reference/statements/error-statement.md)  
 [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
