---
title: 'Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6f70b4c67de892c3b66a0099dae9f618a99b3f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770496"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma
<xref:System.AppDomain.FirstChanceException> Olayı <xref:System.AppDomain> sınıfı bir özel durum bir bildirim almanızı sağlar, önce ortak dil çalışma zamanı için özel durum işleyicileri aramaya başladı.

 Olay, uygulama etki alanı düzeyinde oluşturulur. Bir uygulama etki alanında işlenmeyen bir özel durum başka bir uygulama etki alanında ele alınması için bir iş parçacığı, birden çok uygulama etki alanları geçirebilirsiniz. Uygulama etki alanı özel durumu işleyen kadar olay işleyicisi eklediğiniz her uygulama etki alanında bildirim gerçekleşir.

 Bu makaledeki örneklerde ve yordamları bir uygulama etki alanına sahip basit bir program ve oluşturduğunuz uygulama etki alanında ilk fırsat özel durum bildirimleri alma işlemini göstermektedir.

 Birden çok uygulama etki alanları kapsayan daha karmaşık bir örnek için örneğin bakın <xref:System.AppDomain.FirstChanceException> olay.

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Varsayılan uygulama etki alanında ilk fırsat özel durum bildirimleri alma
 Aşağıdaki yordamda, uygulamanın giriş noktasını `Main()` yöntemi, varsayılan uygulama etki alanında çalışır.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Varsayılan uygulama etki alanında ilk fırsat özel durum bildirimleri göstermek için

1. Tanımlamak için bir olay işleyicisi <xref:System.AppDomain.FirstChanceException> olay, bir lambda kullanarak işlev ve olaya ekleyin. Bu örnekte olay işleyicisi nerede olay işlenen uygulama etki alanı adını ve özel durumun yazdırır <xref:System.Exception.Message%2A> özelliği.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. Bir özel durum ve bunu yakalayıp yakalamayacağınıza. Çalışma zamanı özel durum işleyicisi bulur önce <xref:System.AppDomain.FirstChanceException> olay tetiklenir ve bir ileti görüntüler. Bu ileti özel durum işleyicisi tarafından görüntülenen ileti takip eder.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. Özel durum, ancak bunu yakalamayın. Çalışma zamanı için bir özel durum işleyicisi arar önce <xref:System.AppDomain.FirstChanceException> olay tetiklenir ve bir ileti görüntüler. Uygulama sonlanana için hiçbir özel durum işleyicisi yok.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Bu yordamın ilk üç adımda gösterilen kod tam konsol uygulaması oluşturur. Varsayılan uygulama etki alanı adını adı ve uzantısı .exe dosyasının oluştuğundan uygulama çıktısı, .exe dosyasının adı bağlı olarak değişir. Aşağıdaki örnek çıktı bakın.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Başka bir uygulama etki alanında ilk fırsat özel durum bildirimleri alma
 Programınızı birden fazla uygulama etki alanını içeriyorsa, hangi uygulama etki alanları bildirimlerin seçebilirsiniz.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Oluşturduğunuz bir uygulama etki alanında ilk fırsat özel durum bildirimleri almak için

1. Tanımlamak için bir olay işleyicisi <xref:System.AppDomain.FirstChanceException> olay. Bu örnekte bir `static` yöntemi (`Shared` yöntem Visual Basic'te) olay burada ele uygulama etki alanı adını ve özel durumun yazdırır <xref:System.Exception.Message%2A> özelliği.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. Bir uygulama etki alanı oluşturma ve olay işleyicisi ekleme <xref:System.AppDomain.FirstChanceException> , uygulama etki alanı için olay. Bu örnekte, uygulama etki alanını adlı `AD1`.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     Varsayılan uygulama etki alanında bu olay aynı şekilde işleyebilirsiniz. Kullanım `static` (`Shared` Visual Basic'te) <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> özelliğinde `Main()` varsayılan uygulama etki alanı için bir başvuru almak için.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Uygulama etki alanında ilk fırsat özel durum bildirimleri göstermek için

1. Oluşturma bir `Worker` önceki yordamda oluşturduğunuz uygulama etki alanındaki nesne. `Worker` Sınıfı, ortak olmalıdır ve öğesinden türetilmelidir <xref:System.MarshalByRefObject>, bu makalenin sonundaki tam örnekte gösterildiği gibi.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. Bir yöntemi çağırmak `Worker` bir özel durum nesnesi. Bu örnekte, `Thrower` yöntemi iki kez çağrılır. İlk kez yöntemi bağımsız değişken olan `true`, kendi özel durumu yakalamak yöntem neden olur. Bağımsız değişken ikinci kez olan `false`ve `Main()` yöntemi varsayılan uygulama etki alanındaki özel durumu yakalar.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. Kodda yerleştirin `Thrower` yöntemi kendi özel durum işleme olup olmadığını denetlemek için yöntemi.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a>Örnek
 Aşağıdaki örnekte adlı bir uygulama etki alanı oluşturur `AD1` ve uygulama etki alanına ait bir olay işleyicisi ekler <xref:System.AppDomain.FirstChanceException> olay. Örnek örneği oluşturur `Worker` adlı bir yöntemi çağırır ve uygulama etki alanı sınıfı `Thrower` oluşturan bir <xref:System.ArgumentException>. Bağımsız değişkeninin değeri, bağlı olarak yöntem özel durumu yakalar ya da işlenmesi başarısız olur.

 Her zaman `Thrower` yöntemi bir özel durum atar `AD1`, <xref:System.AppDomain.FirstChanceException> olayı oluşturulur `AD1`, ve olay işleyicisi bir ileti görüntüler. Çalışma zamanı sonra bir özel durum işleyicisi arar. Bu durumda, özel durum işleyici içinde bulunan `AD1`. İkinci durumda, özel durum işlenmemiş `AD1`ve bunun yerine varsayılan uygulama etki alanında yakalanır.

> [!NOTE]
>  Varsayılan uygulama etki alanı adı, yürütülebilir dosya adı ile aynıdır.

 İçin bir işleyici eklediğinizde <xref:System.AppDomain.FirstChanceException> varsayılan uygulama etki alanı, olay için olay gerçekleşti ve varsayılan uygulama etki alanı özel durumu işleyen önce işlenir. Bunu görmek için C# kodu ekleyin. `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (Visual Basic'te `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException`) başına `Main()`.

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="compiling-the-code"></a>Kod Derleniyor

-   Bu örnek, bir komut satırı uygulamasıdır. Derlemek ve Visual Studio'da bu kodu çalıştırmak için C# kodu ekleyin. `Console.ReadLine();` (Visual Basic'te `Console.ReadLine()`) sonunda `Main()`komut penceresi çıktısı okuyabilirsiniz önce kapatılmasını önlemek için.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain.FirstChanceException>
