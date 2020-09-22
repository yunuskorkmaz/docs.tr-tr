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
ms.openlocfilehash: f3f9f5ecb96686fe525e98cf64672d81a3145796
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873271"
---
# <a name="error-statement"></a>Error Deyimi

Bir hata oluşumunun benzetimini yapar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Bölümler  

 `errornumber`  
 Gereklidir. Herhangi bir geçerli hata numarası olabilir.  
  
## <a name="remarks"></a>Açıklamalar  

 `Error`Bildirim, geriye dönük uyumluluk için desteklenir. Yeni kodda, özellikle nesne oluştururken, `Err` `Raise` çalışma zamanı hataları oluşturmak için nesnenin metodunu kullanın.  
  
 `errornumber`Tanımlanmışsa, `Error` `Err` nesne özellikleri aşağıdaki varsayılan değerlere atandıktan sonra ifade hata işleyicisini çağırır:  
  
|Özellik|Değer|  
|--------------|-----------|  
|`Number`|Deyimin bağımsız değişkeni olarak belirtilen değer `Error` . Herhangi bir geçerli hata numarası olabilir.|  
|`Source`|Geçerli Visual Basic projesinin adı.|  
|`Description`|`Error`Bu dize varsa, belirtilen için işlevin dönüş değerine karşılık gelen dize ifadesi `Number` . Dize yoksa, `Description` sıfır uzunluklu bir dize ("") içerir.|  
|`HelpFile`|Uygun Visual Basic Yardım dosyasının tam sürücü, yol ve dosya adı.|  
|`HelpContext`|Özelliğe karşılık gelen hata için uygun Visual Basic Yardım dosyası bağlam KIMLIĞI `Number` .|  
|`LastDLLError`|Sıfır.|  
  
 Herhangi bir hata işleyicisi yoksa veya hiçbiri etkinleştirilmemişse, nesne özelliklerinden bir hata iletisi oluşturulur ve görüntülenir `Err` .  
  
> [!NOTE]
> Bazı Visual Basic ana bilgisayar uygulamaları nesne oluşturamaz. Sınıf ve nesne oluşturup oluşturamayacağını öğrenmek için ana bilgisayar uygulamanızın belgelerine bakın.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `Error` 11 hata numarasını oluşturmak için ifadesini kullanır.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Gereksinimler  

 **Ad alanı:** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Bütünleştirilmiş kod:** Visual Basic çalışma zamanı kitaplığı (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error Deyimi](on-error-statement.md)
- [Resume Deyimi](resume-statement.md)
- [Hata İletileri](../error-messages/index.md)
