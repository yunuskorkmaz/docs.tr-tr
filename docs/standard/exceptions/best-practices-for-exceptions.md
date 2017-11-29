---
title: "Özel Durumlar için En İyi Yöntemler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87f9287c3714416ee5d6b63f3c9db311bb97b131
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2017
---
# <a name="best-practices-for-exceptions"></a>Özel durumlar için en iyi yöntemler

İyi tasarlanmış bir uygulama, özel durumları ve hataları işleyerek uygulama kilitlenmelerini önler. Bu bölüm işleme ve özel durumlar oluşturma en iyi uygulamaları açıklar.

## <a name="use-trycatchfinally-blocks"></a>Try/catch/finally bloklarını kullanma

Kullanım `try` / `catch` / `finally` geçici bir özel durum oluşturmak kod blokları. 

İçinde `catch` engeller, her zaman sipariş özel durumlar en az belirli özel.

Kullanım bir `finally` veya kurtarabilirsiniz olup olmadığını, kaynakları temizlemek için blok.

## <a name="handle-common-conditions-without-throwing-exceptions"></a>Özel durumları atma olmadan genel koşullar işleme

Oluşur ancak bir özel durum harekete özel kurtulursunuz bir biçimde işleme göz önünde bulundurun büyük olasılıkla koşulları. Örneğin, zaten kapatılmış bir bağlantıyı kapatın denerseniz elde edersiniz bir `InvalidOperationException`. Kullanarak, önleyebilirsiniz bir `if` deyimi kapatmak denemeden önce bağlantı durumunu kontrol edin.

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

Bağlantı durumu kapatmadan önce denetlemez, yakalayabilir `InvalidOperationException` özel durum.

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

Olayın gerçekleşmesi için ne sıklıkta yapılacağı seçmek için yöntem bağlıdır.

- Olay çok sık oluşmuyorsa, yani gerçekten olağanüstüyse ve bir hatayı gösteriyorsa (beklenmeyen bir dosya sonu gibi), özel durum işlemeyi kullanın. Özel durum işleme kullandığınızda, normal koşullarda daha az kod çalıştırılır.

- Olay düzenli olarak gerçekleştirilir ve normal yürütme bir parçası olarak değerlendirilebilir kodda hata koşulları için kontrol edin. Sık karşılaşılan hata koşulları için işaretlediğinizde, özel durumlar önlemek için daha az kod yürütülür.

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Özel durumlar önlenebilir böylece sınıfları tasarlama

Veya bir özel durum çağrı yapmaktan kaçınmak olanak tanıyan özellikler tetikleyecek bir sınıfı yöntemleri sağlayabilir. Örneğin, bir <xref:System.IO.FileStream> sınıfı dosyasının sonuna ulaşıldı olup olmadığını belirlemenize yardımcı yöntemler sağlar. Bu dosya sonunun okuyorsanız oluşan özel durum önlemek için kullanılabilir. Aşağıdaki örnek, bir özel durum tetiklemeden dosya sonuna kadar okumak gösterilmiştir.

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

Özel durumlar önlemek için başka bir özel durum atma yerine son derece ortak hata durumları için null döndürmek için yoludur. Çok yaygın olan bir hata durumu, denetiminin normal akışı olarak kabul edilebilir. Bu durumda null değer döndürerek, uygulama performansı üzerindeki etkisini en aza indirirsiniz.

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Bir hata kodu döndürüyor yerine özel durumlar oluşturma

Özel durumlar hataları çağırmak için kodu bir dönüş koduyla kontrol kaydetmedi gözden kaçan geçmemektedir emin olun. 

## <a name="use-the-predefined-net-exception-types"></a>Önceden tanımlanmış .NET özel durum türleri kullanma

Önceden tanımlanmış bir yalnızca uygulanmaz zaman yeni bir özel durum sınıfı tanıtır. Örneğin:

- Throw bir <xref:System.InvalidOperationException> bir özellik kümesi veya yöntem çağrısı nesnenin geçerli durumu verilen uygun değilse, özel durum.

- Throw bir <xref:System.ArgumentException> özel durum ya da öğesinden türetilen önceden tanımlanmış sınıflarından <xref:System.ArgumentException> geçersiz parametreler aktarılırsa.

## <a name="end-exception-class-names-with-the-word-exception"></a>Son özel durum sınıfı adları sözcüğü`Exception`

Bir özel durum gerekli olduğunda, uygun şekilde adlandırın ve buradan türetebilir <xref:System.Exception> sınıfı. Örneğin:

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a>Üç oluşturucular özel durum sınıfları içerir

En az üç ortak oluşturucular kendi özel durum sınıfları oluştururken kullanmak: varsayılan oluşturucu, dize ileti alan bir oluşturucu ve dize ileti ve iç özel duruma alan bir oluşturucu.

* <xref:System.Exception.%23ctor>, varsayılan değerleri kullanır.
  
* <xref:System.Exception.%23ctor%28System.String%29>, bir dize ileti kabul eder.  
  
* <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, bir dize ileti ve iç özel duruma kabul.  
  
Bir örnek için bkz: [nasıl yapılır: Create User-Defined özel durumları](how-to-create-user-defined-exceptions.md).

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Kod uzaktan yürüttüğünde özel durum verileri kullanılabilir olduğundan emin olun

Kullanıcı tanımlı özel durumları oluşturduğunuzda, uzaktan yürütme kod için özel durumlar için meta veriler kullanılabilir olduğundan emin olun. 

Örneğin, uygulama etki alanları destekleyen .NET uygulamalarında, uygulama etki alanları arasında özel durumlar oluşabilir. Uygulama etki alanı A aykırı kodu yürütür uygulama etki alanı B oluşturur varsayalım. Uygulama etki alanı için doğru yakalamak ve özel durumu işlemek için bir uygulama etki alanı b tarafından oluşturulan özel durum içeren derlemenin bulamıyor olmalıdır Uygulama etki alanı B bütünleştirilmiş kendi uygulama temel altında bulunan bir özel durum oluşturur, ancak uygulama etki alanı A'ın uygulama temel altında değil, uygulama etki alanı bir özel durum bulmak mümkün olmaz ve ortak dil çalışma zamanı özel durum oluşturacak bir <xref:System.IO.FileNotFoundException> özel durum. Bu durumu önlemek için, özel durum bilgisini içeren derlemeyi iki şekilde dağıtabilirsiniz:

- Derlemeyi iki uygulama etki alanı tarafından paylaşılan ortak bir uygulama temel dizinine koyun.

    \-veya -

- Eğer etki alanları ortak bir uygulama temel dizini paylaşmıyorsa, özel durum bilgisi içeren derlemeyi bir tanımlayıcı ad ile imzalayıp derlemeyi genel bütünleştirilmiş kod önbelleğine dağıtarak.

## <a name="include-a-localized-description-string-in-every-exception"></a>Her bir durum yerelleştirilmiş açıklama dizesi içerir

Kullanıcının gördüğü hata iletisi, oluşturulan özel durumun açıklama dizesi ve olmayan özel durum sınıfı adı elde edilir.

## <a name="use-grammatically-correct-error-messages"></a>Dilbilgisi bakımından doğru hata iletilerini kullanın

Clear cümle yazın ve noktalama bitiş içerir. Bir özel durumun açıklama dizesindeki her cümle nokta ile bitmelidir. Örneğin, "günlüğü tablosu taştı." uygun açıklama dizesi olacaktır.

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Özel durumlar gerektiği gibi ek özellikler sağlar

Bir özel durum (ek açıklama dizesi) için ek özellikler sağlamak yalnızca ek bilgiler nerede yararlı programlı bir senaryo olduğunda. Örneğin, <xref:System.IO.FileNotFoundException> sağlar <xref:System.IO.FileNotFoundException.FileName> özelliği.

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Böylece yığın izlemesi yardımcı olacaktır yer throw deyimleri

Burada özel durum oluşur ve bitişi bildirimi yığın izleme başlangıcı `catch` özel yakalar deyimi.

## <a name="use-exception-builder-methods"></a>Özel durum Oluşturucu yöntemleri kullanın

Bir sınıfın uygulamasında aynı özel durumu farklı yerlerde oluşturması yaygındır. Fazla kodu önlemek için, özel durumu oluşturmak ve döndürmek için yardımcı yöntemler kullanın. Örneğin:

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
Bazı durumlarda, özel durumun Oluşturucusu özel durum oluşturmak için kullanılacak daha uygundur. Genel özel durum sınıfı gibi örneğidir <xref:System.ArgumentException>.

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Bir özel durum atma zaman ara sonuçlarını temizle

Bir yöntemi çağıranlar, bu yöntemde özel durum oluşturulduğunda bunun yan etkileri olmayacağını varsayabilmelidir. Örneğin, bir hesaptan geri alınmasının ve içinde başka bir hesap ürünü para aktarır kodu varsa ve banka yürütülürken bir özel durum, etkin kalmasını mevzuatı istemezsiniz.

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Bu durumu yönetmek için bir banka işlem tarafından oluşturulan tüm özel durumları yakalar ve mevzuatı geri yoldur.

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

Bu örnek kullanımını göstermektedir `throw` arayanlar inceleyin gerek kalmadan sorunun gerçek nedenini görmek daha kolay hale getirebilir özgün özel yeniden vermesini <xref:System.Exception.InnerException> özelliği. Yeni bir özel durum ve iç özel duruma olarak orijinal özel durumu eklemek için kullanılan bir alternatiftir:

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>Ayrıca Bkz.  
[Özel durumlar](index.md)
