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
ms.openlocfilehash: 95137a9f6a4a4a18655b51b95300bfaf93cca193
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333024"
---
# <a name="resume-statement"></a>Resume Deyimi
Bir hata işleme yordamı tamamlandıktan sonra yürütmeyi sürdürür.  
  
 Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Bölümler  
 `Resume`  
 Gerekli. Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimle devam eder. Çağrılan yordamda hata oluştuysa, yürütme son çağrılan ve hata işleme yordamını içeren yordamın dışında devam eden ifadede sürdürülür.  
  
 `Next`  
 İsteğe bağlı. Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimin hemen ardından gelen ifadesiyle devam eder. Çağrılan yordamda hata oluştuysa, yürütme, hata işleme yordamını (veya `On Error Resume Next` ifadesini) içeren yordamın en son çağrıldığı deyimden hemen sonra gelen deyimle devam eder.  
  
 `line`  
 İsteğe bağlı. Yürütme, gerekli `line` bağımsız değişkeninde belirtilen satırda sürdürülür. `line` bağımsız değişkeni bir çizgi etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Hata işleme yordamında dışında herhangi bir yerde `Resume` ifadesini kullanıyorsanız bir hata oluşur.  
  
 `Resume` deyimleri `Try...Catch...Finally` bir ifade içeren herhangi bir yordamda kullanılamaz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir yordamdaki hata işlemeyi sonlandırmak için `Resume` ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür. `Resume` deyimin kullanımını göstermek için 55 hata numarası oluşturulur.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error Deyimi](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
