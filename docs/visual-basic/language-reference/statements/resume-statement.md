---
title: Özgeçmişi ekstresi (Visual Basic)
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
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583270"
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
 İsteğe bağlı. Yürütme, gerekli `line` bağımsız değişkeninde belirtilen satırda sürdürülür. @No__t_0 bağımsız değişkeni bir çizgi etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Yapılandırılmamış özel durum işleme ve `On Error` ve `Resume` deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Hata işleme yordamında dışında herhangi bir yerde `Resume` ifadesini kullanıyorsanız bir hata oluşur.  
  
 @No__t_0 deyimleri `Try...Catch...Finally` bir ifade içeren herhangi bir yordamda kullanılamaz.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir yordamdaki hata işlemeyi sonlandırmak için `Resume` ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür. @No__t_0 deyimin kullanımını göstermek için 55 hata numarası oluşturulur.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error Deyimi](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
