---
title: Resume Deyimi
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
ms.openlocfilehash: 1d03f631893be51529f29af824de0d684bf43804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603788"
---
# <a name="resume-statement"></a>Resume Deyimi
Hata işleme yordamı tamamladıktan sonra yürütme devam ettirir.  
  
 Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Bölümler  
 `Resume`  
 Gerekli. Yordamın aynısını hata işleyicisine hata oluştu, yürütme hataya deyimiyle devam ettirir. Adlı bir yordamda bir hata oluştu, en son hata işleme yordamı içeren yordamı dışında adlı deyimi yürütme sürdürür.  
  
 `Next`  
 İsteğe bağlı. Yordamın aynısını hata işleyicisine hata oluştu, yürütme hemen aşağıdaki hata nedeniyle ifadeyi deyimiyle devam ettirir. Adlı bir yordamda bir hata oluştu, yürütme hemen son hata işleme yordamı içeren yordamı dışında adlı deyimi aşağıdaki deyim ile devam ettirir (veya `On Error Resume Next` deyimi).  
  
 `line`  
 İsteğe bağlı. Yürütme sürdürür gerekli belirtilen satırında `line` bağımsız değişkeni. `line` Bağımsız değişkeni bir satır etiket veya satır numarası ve bu yordamın aynısını hata işleyicisine olması gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Yapılandırılmamış özel durum işleme kullanmak yerine, mümkün olduğunda, kodunuzda yapılandırılmış özel durum işleme kullanmanızı öneririz ve `On Error` ve `Resume` deyimleri. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Kullanırsanız, bir `Resume` deyiminde herhangi bir yere dışında bir hata işleme yordamı, bir hata oluşur.  
  
 `Resume` Deyimi içeren herhangi bir yordamı kullanılamaz bir `Try...Catch...Finally` deyimi.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Resume` hata bir yordamda işleme sonlandırmak ve yürütme hataya deyim ile devam etmek için bildirimi. Hata numarası 55 kullanımını göstermek için oluşturulur `Resume` deyimi.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Error Deyimi](../../../visual-basic/language-reference/statements/error-statement.md)  
 [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
