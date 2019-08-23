---
title: Error bildirisi (Visual Basic)
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
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944451"
---
# <a name="error-statement"></a>Error Deyimi
Bir hata oluşumunun benzetimini yapar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Bölümler  
 `errornumber`  
 Gerekli. Herhangi bir geçerli hata numarası olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bildirim `Error` , geriye dönük uyumluluk için desteklenir. Yeni kodda, özellikle nesne oluştururken, çalışma zamanı hataları oluşturmak `Err` için `Raise` nesnenin metodunu kullanın.  
  
 Tanımlanmışsa, nesne özellikleri aşağıdaki varsayılan değerlere atandıktan sonraifadehataişleyicisiniçağırır:`Error` `Err` `errornumber`  
  
|Özellik|Değer|  
|--------------|-----------|  
|`Number`|`Error` Deyimin bağımsız değişkeni olarak belirtilen değer. Herhangi bir geçerli hata numarası olabilir.|  
|`Source`|Geçerli Visual Basic projesinin adı.|  
|`Description`|Bu dize varsa, belirtilen `Error` `Number`için işlevin dönüş değerine karşılık gelen dize ifadesi. Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.|  
|`HelpFile`|Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.|  
|`HelpContext`|`Number` Özelliğe karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam kimliği.|  
|`LastDLLError`|Sıfırlama.|  
  
 Herhangi bir hata işleyicisi yoksa veya hiçbiri etkinleştirilmemişse, `Err` nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir.  
  
> [!NOTE]
> Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz. Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `Error` 11 hata numarasını oluşturmak için ifadesini kullanır.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Gereksinimler  
 **Uzayına** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Derleme** Visual Basic Çalışma Zamanı Kitaplığı (Microsoft.VisualBasic.dll içinde)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error Deyimi](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume Deyimi](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Hata İletileri](../../../visual-basic/language-reference/error-messages/index.md)
