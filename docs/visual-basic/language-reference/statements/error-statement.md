---
title: Error Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351242"
---
# <a name="error-statement"></a>Error Deyimi
Bir hata oluşumunun benzetimini yapar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Bölümler  
 `errornumber`  
 Gerekli. Herhangi bir geçerli hata numarası olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Error` deyimleri geriye dönük uyumluluk için desteklenir. Yeni kodda, özellikle nesne oluştururken, çalışma zamanı hataları oluşturmak için `Err` nesnenin `Raise` metodunu kullanın.  
  
 `errornumber` tanımlanmışsa, `Error` ifade, `Err` nesnesinin özelliklerine aşağıdaki varsayılan değerler atandıktan sonra hata işleyicisini çağırır:  
  
|Özellik|Value|  
|--------------|-----------|  
|`Number`|`Error` deyimin bağımsız değişkeni olarak belirtilen değer. Herhangi bir geçerli hata numarası olabilir.|  
|`Source`|Geçerli Visual Basic projesinin adı.|  
|`Description`|Bu dize varsa, belirtilen `Number`için `Error` işlevinin dönüş değerine karşılık gelen dize ifadesi. Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.|  
|`HelpFile`|Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.|  
|`HelpContext`|`Number` özelliğine karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam KIMLIĞI.|  
|`LastDLLError`|Sıfırlama.|  
  
 Herhangi bir hata işleyicisi yoksa veya hiçbiri etkin değilse, `Err` nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir.  
  
> [!NOTE]
> Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz. Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, 11 hata numarasını oluşturmak için `Error` ifadesini kullanır.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Ad alanı:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft. VisualBasic. dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume Deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Hata İletileri](../../../visual-basic/language-reference/error-messages/index.md)
