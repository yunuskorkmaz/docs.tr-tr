---
title: "Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8c98f8a1f09488bb2d93c4fda531f695354059a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma
<xref:System.AppDomain.FirstChanceException> Olayı <xref:System.AppDomain> sınıfı bir özel durum bildirimi olanak sağlar, önce ortak dil çalışma zamanı özel durum işleyicileri için arama başladı.  
  
 Olay uygulama etki alanı düzeyinde oluşturulur. Bir uygulama etki alanında işlenmeyen bir özel durum başka bir uygulama etki alanında ele alınması için bir iş parçacığı yürütme birden çok uygulama etki alanları arasında geçiş yapabilir. Uygulama etki alanı özel durumu işler kadar olay işleyicisi eklenen her uygulama etki alanındaki bildirim oluşur.  
  
 Bu makaledeki örnekler ve yordamları bir uygulama etki alanına sahip basit bir program ve oluşturduğunuz uygulama etki alanı ilk fırsat özel durum bildirimleri almak nasıl gösterir.  
  
 Örneğin, birkaç uygulama etki alanları kapsayan daha karmaşık bir örnek için bkz <xref:System.AppDomain.FirstChanceException> olay.  
  
## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Varsayılan uygulama etki alanında ilk fırsat özel durum bildirimleri alma  
 Aşağıdaki yordamda, bir uygulama için giriş noktası `Main()` yöntemi, varsayılan uygulama etki alanında çalışır.  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Varsayılan uygulama etki alanında ilk fırsat özel durum bildirimleri göstermek için  
  
1.  Bir olay işleyicisi tanımlama <xref:System.AppDomain.FirstChanceException> olay, bir lambda kullanarak işlev ve olaya ekleme. Bu örnekte, olay işleyicisi nerede olay işlenmiş uygulama etki alanı adı ve özel durumun yazdırır <xref:System.Exception.Message%2A> özelliği.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]  
  
2.  Bir özel durum ve onu yakalayın. Çalışma zamanı özel durum işleyici bulur önce <xref:System.AppDomain.FirstChanceException> olay tetiklenir ve bir ileti görüntüler. Bu ileti özel durum işleyicisi tarafından görüntülenen ileti tarafından izlenir.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]  
  
3.  Bir özel durum, ancak bunu catch değil. Bir özel durum işleyicisi için çalışma zamanı görünür önce <xref:System.AppDomain.FirstChanceException> olay tetiklenir ve bir ileti görüntüler. Uygulama sonlanana için hiçbir özel durum işleyici yok.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]  
  
     Bu yordamın ilk üç adımda gösterilen kodu tam konsol uygulaması oluşturur. Varsayılan uygulama etki alanı adı .exe dosya uzantısını ve adını oluştuğundan uygulamadan çıktı, .exe dosya adı bağlı olarak değişir. Aşağıdaki örnek çıktı için bakın.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]  
  
## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Başka bir uygulama etki alanında ilk fırsat özel durum bildirimleri alma  
 Programınızı birden fazla uygulama etki alanı varsa, hangi uygulama etki alanları bildirimlerin seçebilirsiniz.  
  
#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Oluşturduğunuz bir uygulama etki alanında ilk fırsat özel durum bildirimleri almak için  
  
1.  Bir olay işleyicisi tanımlama <xref:System.AppDomain.FirstChanceException> olay. Bu örnekte bir `static` yöntemi (`Shared` yöntemi Visual Basic'te) nerede olay işlenmiş uygulama etki alanı adı ve özel durumun yazdırır <xref:System.Exception.Message%2A> özelliği.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]  
  
2.  Uygulama etki alanı oluşturma ve olay işleyicisi ekleme <xref:System.AppDomain.FirstChanceException> olay o uygulama etki alanı. Bu örnekte, uygulama etki alanı adında `AD1`.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]  
  
     Varsayılan uygulama etki alanında bu olay aynı şekilde işleyebilir. Kullanım `static` (`Shared` Visual Basic'te) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> özelliğinde `Main()` varsayılan uygulama etki alanı için bir başvuru alınamıyor.  
  
#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Uygulama etki alanında ilk fırsat özel durum bildirimleri göstermek için  
  
1.  Oluşturma bir `Worker` önceki yordamda oluşturduğunuz uygulama etki alanı nesnesi. `Worker` Sınıfı genel olmalıdır ve öğesinden türetilmelidir <xref:System.MarshalByRefObject>, bu makalenin sonunda eksiksiz örnekte gösterildiği gibi.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]  
  
2.  Bir yöntemi çağırmak `Worker` aykırı nesnesi. Bu örnekte, `Thrower` yöntemi iki kez çağrılır. İlk kez yöntemi değişkendir `true`, kendi özel durumu yakalamak yöntem neden olur. Bağımsız değişken ikincisinde ise, değer `false`ve `Main()` yöntemi özel durum varsayılan uygulama etki alanındaki yakalar.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]  
  
3.  Yerleştirin kodda `Thrower` yöntemi kendi özel durumu işler olup olmadığını denetlemek için yöntem.  
  
     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek adlı bir uygulama etki alanı oluşturur `AD1` ve uygulama etki alanına ait bir olay işleyicisi ekler <xref:System.AppDomain.FirstChanceException> olay. Örnek bir örneğini oluşturur `Worker` sınıfı uygulama etki alanı ve bir yöntem adlı çağrıları `Thrower` oluşturur, bir <xref:System.ArgumentException>. Bağımsız değişken değeri, bağlı olarak yöntemi özel durum yakalar ya da işlenmesi başarısız olur.  
  
 Her zaman `Thrower` yöntemi bir özel durum oluşturur `AD1`, <xref:System.AppDomain.FirstChanceException> olayı oluşturulur `AD1`, ve olay işleyicisi bir ileti görüntüler. Çalışma zamanı sonra bir özel durum işleyici arar. İlk durumda, özel durum işleyici içinde bulunur `AD1`. İkinci durumda, özel durum işlenmemiş `AD1`ve bunun yerine varsayılan uygulama etki alanında yakalandı.  
  
> [!NOTE]
>  Varsayılan uygulama etki alanı adı yürütülebilir dosyanın adını ile aynıdır.  
  
 İçin bir işleyici eklediğinizde <xref:System.AppDomain.FirstChanceException> varsayılan uygulama etki alanı, olay için olay gerçekleşti ve varsayılan uygulama etki alanı özel durumu işler önce işlenir. Bu görmek için C# kod ekleme `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (Visual Basic'te `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) başında `Main()`.  
  
 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Bu örnek, bir komut satırı uygulamasıdır. Derlemek ve bu kodu çalıştırmak için [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], C# kod ekleme `Console.ReadLine();` (Visual Basic'te `Console.ReadLine()`) sonunda `Main()`, çıktı okuyabilmesi kapatma komut penceresinde önlemek için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.AppDomain.FirstChanceException>
