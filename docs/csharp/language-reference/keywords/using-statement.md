---
title: using Deyimi (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7bf9138721ecee63c65c2e39922aee96b1dfaa41
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208410"
---
# <a name="using-statement-c-reference"></a>using Deyimi (C# Başvurusu)
Doğru kullanımı sağlar kullanışlı bir sözdizimi sağlar <xref:System.IDisposable> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir `using` deyimi.  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.IO.File> ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara (Bu örnek dosya tanıtıcıları ve cihaz bağlamları) erişim yönetilen türlerine örnek olarak verilebilir. Yönetilmeyen kaynakları ve bunları saklayan sınıf kitaplığı türleri pek çok değişik vardır. Tüm türleri uygulamalıdır <xref:System.IDisposable> arabirimi.  
  
Zaman ömrü bir `IDisposable` nesnesidir tek bir yöntem sınırlı, bildirme ve içinde örneği `using` deyimi. `using` Deyimi çağrıları <xref:System.IDisposable.Dispose%2A> doğru bir şekilde ve (daha önce gösterildiği gibi kullandığınız zaman) nesnesi üzerinde yöntemi de neden nesnenin kendisini kapsamının dışına gitmek için hemen <xref:System.IDisposable.Dispose%2A> olarak adlandırılır. İçinde `using` bloğu, nesneyi salt okunur ve yeniden atandığında veya değiştirilemez.  
  
 `using` Deyimi sağlar <xref:System.IDisposable.Dispose%2A> içinde bir özel durum oluştuğunda dahi adlı `using` bloğu. Nesne içinde koyarak aynı sonucu elde edebilirsiniz bir `try` bloğu ve ardından çağırma <xref:System.IDisposable.Dispose%2A> içinde bir `finally` engelle; aslında, bu nasıl `using` deyimi derleyici tarafından çevrilir. Kod örneği, aşağıdaki kodu önceden derleme zamanında genişletir. (nesne için sınırlı kapsamı oluşturmak için ek süslü ayraçlar unutmayın):  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 Hakkında daha fazla bilgi için `try` - `finally` deyimi, bkz: [try-finally](try-finally.md) konu.
  
 İçinde bir türü birden çok örneğini bildirilebilir `using` deyimi, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Kaynak nesne örneği ve daha sonra değişkeni geçirin `using` deyimi değildir, ancak bu en iyi yöntem. Bu durumda, Denetim bırakır sonra `using` engellemek, kapsamdaki nesne kalır ancak büyük olasılıkla yönetilmeyen kaynaklarına erişim yok. Diğer bir deyişle, onu tam olarak artık başlatıldı. Nesne dışında kullanmayı denerseniz `using` engellemek, bir özel durum oluşturulmasına neden risk. Bu nedenle, nesne örneğini oluşturmak genellikle daha iyi `using` deyimi ve bunun kapsamına sınırlamak `using` bloğu.  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
Atma hakkında daha fazla bilgi için `IDisposable` nesneleri bkz [IDisposable uygulayan nesneler kullanma](../../../standard/garbage-collection/using-objects.md).

## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [using Yönergesi](../../../csharp/language-reference/keywords/using-directive.md)  
 [Atık Toplama](../../../standard/garbage-collection/index.md)  
 [IDisposable uygulayan nesneler kullanma](../../../standard/garbage-collection/using-objects.md)  
 [IDisposable arabirimi](xref:System.IDisposable)
