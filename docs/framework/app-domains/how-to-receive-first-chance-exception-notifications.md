---
title: 'Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma'
description: CLR özel durum işleyicilerini aramadan önce AppDomain sınıfının FirstChanceException olayı aracılığıyla .NET 'teki ilk şans özel durum bildirimlerini alın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- first-chance exception notifications
- exceptions, first chance notifications
ms.assetid: 66f002b8-a97d-4a6e-a503-2cec01689113
ms.openlocfilehash: e8b5ae5fb69c7befd329316aee11523f79d73fcd
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104736"
---
# <a name="how-to-receive-first-chance-exception-notifications"></a>Nasıl yapılır: İlk Fırsat Özel Durum Bildirimleri Alma
<xref:System.AppDomain.FirstChanceException>Sınıfının olayı, <xref:System.AppDomain> ortak dil çalışma zamanı özel durum işleyicilerini aramaya başlamadan önce bir özel durumun oluşturulduğu uyarısını almanızı sağlar.

 Olay, uygulama etki alanı düzeyinde oluşturulur. Yürütmenin bir iş parçacığı birden çok uygulama etki alanından geçirebilir, bu nedenle bir uygulama etki alanında işlenmemiş bir özel durum başka bir uygulama etki alanında işlenebilir. Bildirim, bir uygulama etki alanı özel durumu işleyene kadar, olay için bir işleyici ekleyen her uygulama etki alanında oluşur.

 Bu makaledeki yordamlar ve örnekler, tek bir uygulama etki alanı olan basit bir programda ve oluşturduğunuz bir uygulama etki alanında ilk şans özel durum bildirimlerinin nasıl alınacağını gösterir.

 Birden çok uygulama etki alanına yayılan daha karmaşık bir örnek için, olay için örneğe bakın <xref:System.AppDomain.FirstChanceException> .

## <a name="receiving-first-chance-exception-notifications-in-the-default-application-domain"></a>Varsayılan uygulama etki alanında Ilk şans özel durum bildirimleri alma
 Aşağıdaki yordamda uygulama için giriş noktası, `Main()` yöntemi, varsayılan uygulama etki alanında çalışır.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-default-application-domain"></a>Varsayılan uygulama etki alanındaki ilk şans özel durum bildirimlerini göstermek için

1. <xref:System.AppDomain.FirstChanceException>Bir Lambda işlevi kullanarak olay için bir olay işleyicisi tanımlayın ve olaya ekleyin. Bu örnekte olay işleyicisi, olayın işlendiği uygulama etki alanının adını ve özel durumun <xref:System.Exception.Message%2A> özelliğini yazdırır.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#2)]

2. Bir özel durum oluşturun ve yakalayın. Çalışma zamanı özel durum işleyicisini bulduktan önce, <xref:System.AppDomain.FirstChanceException> olay tetiklenir ve bir ileti görüntüler. Bu iletinin ardından özel durum işleyicisi tarafından görüntülenen ileti gelir.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#3)]

3. Bir özel durum oluşturur, ancak bunu yakalamaz. Çalışma zamanı bir özel durum işleyicisini ararken, <xref:System.AppDomain.FirstChanceException> olay tetiklenir ve bir ileti görüntüler. Bir özel durum işleyici yoktur, bu nedenle uygulama sonlanır.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#4)]

     Bu yordamın ilk üç adımda gösterilen kod, bir konsol uygulaması oluşturur. Uygulamanın çıktısı,. exe dosyasının adına bağlı olarak değişir, çünkü varsayılan uygulama etki alanının adı. exe dosyasının adı ve uzantısından oluşur. Örnek çıktı için aşağıdakilere bakın.

     [!code-csharp[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto_simple#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto_simple/vb/example.vb#5)]

## <a name="receiving-first-chance-exception-notifications-in-another-application-domain"></a>Başka bir uygulama etki alanında birinci şans özel durum bildirimleri alma
 Programınız birden fazla uygulama etki alanı içeriyorsa, hangi uygulama etki alanlarının bildirim alacağını seçebilirsiniz.

#### <a name="to-receive-first-chance-exception-notifications-in-an-application-domain-that-you-create"></a>Oluşturduğunuz bir uygulama etki alanında ilk şans özel durum bildirimleri almak için

1. Olay için bir olay işleyicisi tanımlayın <xref:System.AppDomain.FirstChanceException> . Bu örnek, `static` `Shared` olayın işlendiği uygulama etki alanının adını ve özel durumun özelliğini yazdıran bir yöntemi (Visual Basic yöntemi) kullanır <xref:System.Exception.Message%2A> .

     [!code-csharp[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#3)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#3)]

2. Uygulama etki alanı oluşturun ve olay işleyicisini <xref:System.AppDomain.FirstChanceException> Bu uygulama etki alanı için olaya ekleyin. Bu örnekte, uygulama etki alanı olarak adlandırılır `AD1` .

     [!code-csharp[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#2)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#2)]

     Bu olayı varsayılan uygulama etki alanında aynı şekilde işleyebilirsiniz. `static` `Shared` <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> `Main()` Varsayılan uygulama etki alanına bir başvuru almak için içindeki (Visual Basic) özelliğini kullanın.

#### <a name="to-demonstrate-first-chance-exception-notifications-in-the-application-domain"></a>Uygulama etki alanındaki ilk şans özel durum bildirimlerini göstermek için

1. `Worker`Önceki yordamda oluşturduğunuz uygulama etki alanında bir nesne oluşturun. `Worker`Sınıf ortak olmalıdır ve <xref:System.MarshalByRefObject> Bu makalenin sonundaki tüm örnekte gösterildiği gibi öğesinden türetilmelidir.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#4)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#4)]

2. `Worker`Bir özel durum oluşturan nesnenin yöntemini çağırın. Bu örnekte, `Thrower` yöntemi iki kez çağrılır. İlk kez metot bağımsız değişkeni, `true` yönteminin kendi özel durumunu yakalamasına neden olur. İkinci kez bağımsız değişken olur `false` ve `Main()` yöntemi varsayılan uygulama etki alanındaki özel durumu yakalar.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#6)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#6)]

3. Yöntemin `Thrower` kendi özel durumunu işlediğini denetlemek için yöntemine kod koyun.

     [!code-csharp[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#5)]
     [!code-vb[System.AppDomain.FirstChanceException_howto#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#5)]

## <a name="example"></a>Örnek
 Aşağıdaki örnek adlı bir uygulama etki alanı oluşturur `AD1` ve uygulama etki alanının olayına bir olay işleyicisi ekler <xref:System.AppDomain.FirstChanceException> . Örnek, `Worker` uygulama etki alanında sınıfının bir örneğini oluşturur ve ' ı oluşturan adlı bir yöntemi çağırır `Thrower` <xref:System.ArgumentException> . Bağımsız değişkeninin değerine bağlı olarak, yöntemi özel durumu yakalar veya işleme başarısız olur.

 `Thrower`Yöntemi ' de bir özel durum oluşturduğunda, `AD1` olay ' <xref:System.AppDomain.FirstChanceException> de oluşturulur `AD1` ve olay işleyicisi bir ileti görüntüler. Çalışma zamanı daha sonra bir özel durum işleyicisi arar. İlk durumda, özel durum işleyicisi içinde bulunur `AD1` . İkinci durumda, özel durum ' de işlenmemiş olur `AD1` ve bunun yerine varsayılan uygulama etki alanında yakalanır.

> [!NOTE]
> Varsayılan uygulama etki alanının adı, yürütülebilir dosyanın adı ile aynıdır.

 <xref:System.AppDomain.FirstChanceException>Varsayılan uygulama etki alanına olay için bir işleyici eklerseniz, varsayılan uygulama etki alanı özel durumu işleymadan önce olay tetiklenir ve işlenir. Bunu görmek için, C# kodunu `AppDomain.CurrentDomain.FirstChanceException += FirstChanceException;` (Visual Basic, `AddHandler AppDomain.CurrentDomain.FirstChanceException, FirstChanceException` ) öğesinin başına ekleyin `Main()` .

 [!code-csharp[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/cs/example.cs#1)]
 [!code-vb[System.AppDomain.FirstChanceException_howto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.firstchanceexception_howto/vb/example.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.AppDomain.FirstChanceException>
