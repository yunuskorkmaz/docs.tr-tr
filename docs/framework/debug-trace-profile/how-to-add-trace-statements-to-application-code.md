---
title: "Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5dd46da24c379a7900dff0dc482577195f5f4c23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-trace-statements-to-application-code"></a>Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme
İzleme için en sık kullanılan yöntemler dinleyici çıktı yazmak için yöntemler şunlardır: **yazma**, **Writeıf**, **WriteLine**, **Writelineıf**, **Assert**, ve **başarısız**. Bu yöntemleri iki kategoriye ayrılabilir: **yazma**, **WriteLine**, ve **başarısız** tüm çıktı koşulsuz, ancak yayma **Writeıf**, **Writelineıf**, ve **Assert** Boolean koşulu test ve yazma ya da koşul değerine göre yazma. **Writeıf** ve **Writelineıf** koşul ise, çıktı yayma `true`, ve **Assert** koşul ise çıktıyı yayar `false`.  
  
 İzleme ve hata ayıklama stratejisi tasarlarken, aramak için çıktı nasıl istediğinizi hakkında düşünmelisiniz. Birden çok **yazma** ilgisiz bilgilerle doldurulmuş deyimleri okunması zor bir günlük oluşturur. Diğer taraftan, kullanarak **WriteLine** ilişkili ifadeleri koymak için ayrı satırlara hangi bilgilerin birlikte ait ayırt etmek zorlaştıran. Genel olarak, çoklu kullanmak **yazma** tek bir bilgilendirici ileti oluşturmak ve kullanmak için birden fazla kaynaktan bilgileri birleştirmek istediğinizde deyimleri **WriteLine** oluşturmak istediğinizde deyimi bir tek, tam iletisi.  
  
### <a name="to-write-a-complete-line"></a>Tam bir satır yazmak için  
  
1.  Arama <xref:System.Diagnostics.Trace.WriteLine%2A> veya <xref:System.Diagnostics.Trace.WriteLineIf%2A> yöntemi.  
  
     Böylece sonraki iletiyi tarafından döndürülen satır başı bu yöntem, ileti sonuna eklenir **yazma**, **Writeıf**, **WriteLine**, veya  **Writelineıf** aşağıdaki satırda başlar:  
  
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
  
     Sonraki iletiyi put bir **yazma**, **Writeıf**, **WriteLine**, veya **Writelineıf** tarafından put ileti aynı satırda başlar **yazma** veya **Writeıf** deyimi:  
  
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
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a>Doğrulamak için bu belirli koşullar, önce veya sonra bir yöntem yürütülmeye mevcut  
  
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
    >  Kullanabileceğiniz **Assert** izleme ve hata ayıklama ile. Bu örnekte tüm dinleyici için çağrı yığını çıkarır **dinleyicileri** koleksiyonu. Daha fazla bilgi için bkz: [yönetilen koddaki onaylar](/visualstudio/debugger/assertions-in-managed-code) ve <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>  
 [İzleme ve uygulamaları](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Nasıl yapılır: oluşturma ve başlatma izleme anahtarları](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [İzleme anahtarları](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [İzleme dinleyicileri](../../../docs/framework/debug-trace-profile/trace-listeners.md)
