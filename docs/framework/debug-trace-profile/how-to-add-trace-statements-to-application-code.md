---
title: 'Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 9903a0357d1d8ceade21b590fd54c8cab517f134
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174751"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme
İzleme için en sık kullanılan yöntemler dinleyicilere çıktı yazma yöntemleridir: **Write** **, WriteIf**, **WriteLine**, **WriteLineIf**, Assert , **ve** **Fail**. Bu yöntemler iki kategoriye ayrılabilir: **Yazma**, **WriteLine**, ve **Fail** tüm koşulsuz çıkış yontmak, oysa **WriteIf**, **WriteLineIf**, ve Test bir Boolean durum **assert** ve yazma veya durumun değerine göre yazmayın. **WriteIf** ve **WriteLineIf** koşul ise `true`çıktı yayıyorum ve koşul ise `false` **Assert** çıktı yayır.  
  
 İzleme ve hata ayıklama stratejinizi tasarlarken, çıktının nasıl görünmesini istediğinizi düşünmelisiniz. İlişkisiz bilgilerle dolu birden çok **Yazma** deyimleri, okunması zor bir günlük oluşturur. Diğer taraftan, ilgili ifadeleri ayrı satırlara koymak için **WriteLine'ı** kullanmak, hangi bilgilerin birbirine ait olduğunu ayırt etmeyi zorlaştırabilir. Genel olarak, tek bir bilgilendirici ileti oluşturmak için birden çok kaynaktan gelen bilgileri birleştirmek istediğinizde birden çok **Yazma** deyimi kullanın ve tek bir tam ileti oluşturmak istediğinizde **WriteLine** deyimini kullanın.  
  
### <a name="to-write-a-complete-line"></a>Tam bir satır yazmak için  
  
1. Arama <xref:System.Diagnostics.Trace.WriteLine%2A> veya <xref:System.Diagnostics.Trace.WriteLineIf%2A> yöntemi.  
  
     Bir satır geri dönüşü iletinin sonuna eklenir, bu yöntem döndürür, böylece sonraki ileti **Write**, **WriteIf**, WriteLine , veya **WriteLineIf**tarafından döndürülür aşağıdaki satırda başlar: **WriteLineIf**  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a>Kısmi satır yazmak için  
  
1. Arama <xref:System.Diagnostics.Trace.Write%2A> veya <xref:System.Diagnostics.Trace.WriteIf%2A> yöntemi.  
  
     Write , **WriteIf**, **WriteLine** **WriteLine**, veya **WriteLineIf** tarafından söndürülen bir sonraki ileti, **Writeif** **deyimi** tarafından söndürülen iletiyle aynı satırda başlar:  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Bir yöntemi yürütmeden önce veya sonra belirli koşulların mevcut olduğunu doğrulamak için  
  
1. <xref:System.Diagnostics.Trace.Assert%2A> Yöntemi ara.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > Hem izleme hem de hata ayıklama ile **Assert'ı** kullanabilirsiniz. Bu örnek, çağrı yığınını **Dinleyicikoleksiyonundaki** herhangi bir dinleyiciye çıkar. Daha fazla bilgi için [Yönetilen Kod'daki İddialar](/visualstudio/debugger/assertions-in-managed-code) ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [İzleme ve İşaretleme Uygulamaları](tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma](how-to-create-initialize-and-configure-trace-switches.md)
- [İzleme Anahtarları](trace-switches.md)
- [İz Dinleyicileri](trace-listeners.md)
