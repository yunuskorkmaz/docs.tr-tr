---
title: "Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Değiştirilebilir ve Değiştirilemez Bağımsız Değişkenler Arasındaki Farklar (Visual Basic)
Bir yordam çağrısı, genellikle bir veya daha fazla bağımsız değişken için geçirdiğiniz. Her bağımsız bir temel programlama öğeye karşılık gelir. Temel alınan öğeleri ve bağımsız değişkenler kendilerini değiştirilebilir veya değiştirilemez olabilir.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Değiştirilebilir ve değiştirilemez öğeleri  
 Bir programlama öğesi ya da olabilir bir *değiştirilebilir öğesi*, değişti, değeri olabilir veya bir *değiştirilemez öğesi*, oluşturulduktan sonra bir sabit değere sahip.  
  
 Aşağıdaki tabloda, değiştirilebilir ve değiştirilemez programlama öğeleri listeler.  
  
|Değiştirilebilir öğeleri|Değiştirilemez öğeleri|  
|-------------------------|----------------------------|  
|Salt okunur dışında nesne değişkenleri (yordamların içinde bildirilen), yerel değişkenleri dahil|Salt okunur değişkenler, alanlar ve Özellikler|  
|Salt okunur dışında alanları (üye değişkenleri) modülleri, sınıflar ve yapılar|Sabit ve değişmez değerleri|  
|Salt okunur dışında özellikleri|Numaralandırma üyeleri|  
|Dizi öğeleri|Deyimler (öğelerini değiştirilebilir olsa bile)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Değiştirilebilir ve değiştirilemez bağımsız değişkenler  
 A *değiştirilebilir bağımsız değişkeni* değiştirilebilir ve temel bir öğesiyle biridir. Çağrıyı yapan kod herhangi bir zamanda yeni bir değer depolayabilir ve bağımsız değişken geçirirseniz [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), yordamdaki kod çağıran kodu temel alınan öğe de değiştirebilirsiniz.  
  
 A *değiştirilemez bağımsız değişkeni* değiştirilemez bir temel öğeye sahip ya da geçirilen [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Değiştirilebilir öğesi olsa bile, yordamı çağıran kodu, temel alınan öğe değiştirilemiyor. Bunu değiştirilemez bir öğeyse, çağrıyı yapan kod onu değiştiremezsiniz.  
  
 Değişiklik çağıran kodu temel alınan öğe etkilemez ancak bu adlı yordamı değiştirilemez bağımsız değişkeni yerel kopyasını değiştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Parametreler ve bağımsız değişkenler](./procedure-parameters-and-arguments.md)  
 [Nasıl yapılır: bir yordama bağımsız değişkenler geçirme](./how-to-pass-arguments-to-a-procedure.md)  
 [Bağımsız değişkenleri değere ve başvuruya göre geçirme](./passing-arguments-by-value-and-by-reference.md)  
 [Değere ve başvuruya göre bağımsız değişken geçirme arasındaki farklar](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkeninin değerini değiştirme](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Nasıl yapılır: bir yordam bağımsız değişkenini değer değişikliklerine karşı koruma](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Nasıl yapılır: bağımsız değişkeni değere göre geçirilecek şekilde zorlama](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Bağımsız değişkenleri konuma göre ve ada göre geçirme](./passing-arguments-by-position-and-by-name.md)  
 [Değer türleri ve başvuru türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
