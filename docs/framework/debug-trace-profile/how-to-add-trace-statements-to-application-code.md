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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f45259623d4a481e635ac1b54ecb9a17497ab5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204100"
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme
İzleme için en sık kullanılan yöntemleri çıkış dinleyicileri için yazma yöntemleri şunlardır: **Yazma**, **Writeıf**, **WriteLine**, **Writelineıf**, **Assert**, ve **başarısız**. Bu yöntemleri iki kategoriye ayrılabilir: **Yazma**, **WriteLine**, ve **başarısız** tüm çıkış koşulsuz, oysa yayma **Writeıf**, **Writelineıf**ve  **Assert** bir Boolean koşulu test yazma ve koşul değerine göre yazma. **Writeıf** ve **Writelineıf** koşul ise çıktı yayma `true`, ve **Assert** koşul ise, çıktıyı yayar `false`.  
  
 İzleme ve hata ayıklama stratejisi tasarlarken, aramak için çıkış biçimini hakkında almalısınız. Birden çok **yazma** ilgisiz bilgilerle doldurulmuş deyimleri okunması zor bir günlük oluşturur. Öte yandan, kullanarak **WriteLine** ilgili deyimleri koymak için ayrı satırlara, hangi bilgilerin birlikte ait ayırt etmek zor duruma getirebilir. Genel olarak, birden çok kullanın **yazma** tek bir bilgilendirici ileti oluşturmak ve kullanmak için birden fazla kaynaktan bilgileri birleştirmek istediğinizde deyimleri **WriteLine** oluşturmak istediğinizde deyimi bir tek ve eksiksiz iletisi.  
  
### <a name="to-write-a-complete-line"></a>Tam bir satır yazmak için  
  
1.  Arama <xref:System.Diagnostics.Trace.WriteLine%2A> veya <xref:System.Diagnostics.Trace.WriteLineIf%2A> yöntemi.  
  
     Böylece sonraki iletiyi tarafından döndürülen bir satır başı, bu yöntem tarafından döndürülen ileti sonuna eklenir **yazma**, **Writeıf**, **WriteLine**, veya  **Writelineıf** satırında başlar:  
  
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
  
### <a name="to-write-a-partial-line"></a>Kısmi bir satır yazmak için  
  
1.  Arama <xref:System.Diagnostics.Trace.Write%2A> veya <xref:System.Diagnostics.Trace.WriteIf%2A> yöntemi.  
  
     Sonraki iletiyi bırakırsınız bir **yazma**, **Writeıf**, **WriteLine**, veya **Writelineıf** tarafından put ileti ile aynı satırda başlayacak **yazma** veya **Writeıf** deyimi:  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Doğrulamak için belirli koşullar önce veya sonra bir yöntem yürütülmeye var  
  
1.  Çağrı <xref:System.Diagnostics.Trace.Assert%2A> yöntemi.  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  Kullanabileceğiniz **Assert** izleme ve hata ayıklama. Bu örnek herhangi bir dinleyici için çağrı yığınını çıkarır **dinleyicileri** koleksiyonu. Daha fazla bilgi için [yönetilen koddaki onaylar](/visualstudio/debugger/assertions-in-managed-code) ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [İzleme Uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [Nasıl yapılır: İzleme Anahtarları Oluşturma ve Başlatma](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [İzleme Anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [İz Dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
