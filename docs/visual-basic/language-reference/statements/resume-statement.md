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
ms.openlocfilehash: 3f49f05f1deb2027b03bbf3443ca44f30c44344e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404219"
---
# <a name="resume-statement"></a>Resume Deyimi
Bir hata işleme yordamı tamamlandıktan sonra yürütmeyi sürdürür.  
  
 Yapılandırılmamış özel durum işleme ve ve deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` `Resume` . Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Bölümler  
 `Resume`  
 Gereklidir. Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimle devam eder. Çağrılan yordamda hata oluştuysa, yürütme son çağrılan ve hata işleme yordamını içeren yordamın dışında devam eden ifadede sürdürülür.  
  
 `Next`  
 İsteğe bağlı. Hata işleyicisiyle aynı yordamda hata oluştuysa, yürütme hataya neden olan deyimin hemen ardından gelen ifadesiyle devam eder. Çağrılan yordamda hata oluştuysa, yürütme, hata işleme yordamını (veya ifadesini) içeren yordamın en son çağrıldığı deyimin hemen sonrasında ifadesiyle devam eder `On Error Resume Next` .  
  
 `line`  
 İsteğe bağlı. Yürütme, gerekli bağımsız değişkende belirtilen satırda sürdürülür `line` . `line`Bağımsız değişken bir satır etiketi veya satır numarasıdır ve hata işleyicisiyle aynı yordamda olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Yapılandırılmamış özel durum işleme ve ve deyimlerini kullanmak yerine kodunuzda yapılandırılmış özel durum işlemeyi kullanmanızı öneririz `On Error` `Resume` . Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](try-catch-finally-statement.md).  
  
 Bir `Resume` ifadeyi hata işleme yordamında dışında bir yerde kullanıyorsanız bir hata oluşur.  
  
 `Resume`İfade, bir ifade içeren herhangi bir yordamda kullanılamaz `Try...Catch...Finally` .  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Resume` bir yordamda hata işlemeyi sonlandırmak için ifadesini kullanır ve ardından hataya neden olan deyimle yürütmeyi sürdürür. Deyimin kullanımını göstermek için 55 hata numarası oluşturulur `Resume` .  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Gereksinimler  
 **Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](try-catch-finally-statement.md)
- [Error Deyimi](error-statement.md)
- [On Error Deyimi](on-error-statement.md)
