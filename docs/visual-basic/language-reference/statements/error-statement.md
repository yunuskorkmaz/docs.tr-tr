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
ms.openlocfilehash: 3ecfe18392de15dc937d90565b49641415dd7e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603892"
---
# <a name="error-statement"></a>Error Deyimi
Bir hata oluşması benzetimini yapar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Bölümler  
 `errornumber`  
 Gerekli. Herhangi bir geçerli hata sayı olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `Error` Deyimi, geriye dönük uyumluluk için desteklenir. Özellikle nesneleri oluştururken, yeni kodda, kullanın `Err` nesnenin `Raise` çalışma zamanı hataları oluşturmak için yöntem.  
  
 Varsa `errornumber` tanımlanan `Error` deyimi özelliklerini sonra hata işleyici çağırır `Err` nesne aşağıdaki varsayılan değerler atanır:  
  
|Özellik|Değer|  
|--------------|-----------|  
|`Number`|Bağımsız değişkeni olarak belirtilen değeri `Error` deyimi. Herhangi bir geçerli hata sayı olabilir.|  
|`Source`|Geçerli Visual Basic proje adı.|  
|`Description`|Dize ifadesi dönüş değerine karşılık gelen `Error` işlevi için belirtilen `Number`, bu dize varsa. Dize mevcut değilse `Description` sıfır uzunlukta bir dize içeriyor ("").|  
|`HelpFile`|Tam sürücü, yol ve uygun Visual Basic Yardım dosyasının dosya adı.|  
|`HelpContext`|Visual Basic uygun Yardım dosyası hata karşılık gelen için bağlam kimliği `Number` özelliği.|  
|`LastDLLError`|Sıfır.|  
  
 Hiçbir hata işleyici olup olmadığını veya hiçbiri etkinleştirilirse, hata iletisi oluşturulur ve gelen görüntülenen olmadığını `Err` nesne özellikleri.  
  
> [!NOTE]
>  Bazı Visual Basic konak uygulamaların nesneler oluşturamaz. Bunu sınıflar ve nesneler oluşturabilirsiniz olup olmadığını belirlemek için ana bilgisayar uygulamanızın belgelerine bakın.  
  
## <a name="example"></a>Örnek  
 Bu örnekte `Error` hata numarası 11 oluşturmak için ifade.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Derleme:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [Resume Deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Hata İletileri](../../../visual-basic/language-reference/error-messages/index.md)
