---
title: Elden Çıkarma yöntemini uygulama
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: f3d3269ccf56954f963762503d2bc1c53b9e6b83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78238994"
---
# <a name="implementing-a-dispose-method"></a>Elden Çıkarma yöntemini uygulama

Uygulamanız <xref:System.IDisposable.Dispose%2A> tarafından kullanılan yönetilmeyen kaynakları serbest bırakmak için bir yöntem uygularsınız. .NET çöp toplayıcısı yönetilmeyen belleği ayırmaz veya serbest bırakmaz.  
  
Bir nesneyi atmak için desen, bir [elden çıkarma deseni](implementing-dispose.md)olarak adlandırılır, bir nesnenin ömrüne sıra yıkar. Dispose deseni yalnızca yönetilmeyen kaynaklara erişen, dosya ve kanal tanıtıcıları, kayıt defteri tanıtıcıları, bekleme tanıtıcıları veya yönetilmeyen bellek bloğu işaretçileri gibi nesneler için kullanılır. Bunun nedeni, çöp toplayıcısının kullanılmayan yönetilen nesneleri geri kazanmada çok etkili olması, fakat yönetilmeyen nesneleri geri kazanamamasıdır.  
  
Dispose deseninin iki çeşidi vardır:  
  
- Bir türün güvenli bir tanıtıcıda kullandığı yönetilen olmayan her kaynağı <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>(diğer bir sınıfta) sararsınız. Bu durumda, <xref:System.IDisposable> arabirimi ve ek `Dispose(Boolean)` bir yöntem uygularsınız. Bu önerilen varyasyondur ve <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi geçersiz kılmayı gerektirmez.  
  
  > [!NOTE]
  > Ad <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.SafeHandle>alanı, [güvenli iş tanıtıcıları kullanma](#SafeHandles) bölümünde listelenen sınıflar kümesini sağlar. Yönetilmeyen kaynağınızı serbest bırakmak için uygun bir sınıf bulamazsanız, kendi alt <xref:System.Runtime.InteropServices.SafeHandle>sınıfınızı uygulayabilirsiniz.  
  
- Arabirimi <xref:System.IDisposable> ve ek `Dispose(Boolean)` bir yöntemi uygularsınız ve <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi de geçersiz kılarsınız. Uygulamanız türünün bir tüketicisi tarafından çağrılmazsa, yönetilmeyen kaynakların elden çıkarılmasını sağlamak için geçersiz kılmanız <xref:System.Object.Finalize%2A> <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> gerekir. Önceki madde işaretinde tartışılan önerilen tekniği <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> kullanırsanız, sınıf bunu sizin adınıza yapar.  
  
Kaynakların her zaman uygun şekilde temizlenmesini <xref:System.IDisposable.Dispose%2A> sağlamak için, bir yöntem özel durum atmadan birden çok kez çağrılabilir olmalıdır.  
  
<xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> Yöntem için sağlanan kod örneği, çöp toplamanın bir sonlandırıcının çalışmasına nasıl neden olabileceğini gösterirken, nesneye veya üyelerine yönelik yönetilmeyen bir başvuru hala kullanılıyor. Nesneyi, geçerli yordamın başlangıcından bu yöntemin çağrıldığı noktaya kadar çöp toplama için uygun hale getirmek için kullanmak <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> mantıklı olabilir.
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() ve Dispose(Boolean)  

Arabirim, <xref:System.IDisposable> tek bir parametresiz yöntemin uygulanmasını <xref:System.IDisposable.Dispose%2A>gerektirir. Ancak, bertaraf deseni `Dispose` uygulanması için iki yöntem gerektirir:  
  
- Hiçbir parametresi`NonInheritable` olmayan genel <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sanal olmayan (Visual Basic' de) uygulaması.  
  
- `Overridable` `Dispose`  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Elden Çıkarma() aşırı yük

Çünkü genel, sanal olmayan`NonInheritable` (Visual Basic), `Dispose` parametresiz yöntem türünden bir tüketici tarafından çağrılır, amacı yönetilmeyen kaynakları serbest ve sonlandırıcı, varsa, çalıştırmak zorunda olmadığını belirtmektir. Bu nedenle, standart bir uygulaması vardır:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Yöntem `Dispose` tüm nesne temizleme gerçekleştirir, bu nedenle çöp toplayıcı artık <xref:System.Object.Finalize%2A?displayProperty=nameWithType> nesnelerin geçersiz kılma aramak gerekir. Bu nedenle, <xref:System.GC.SuppressFinalize%2A> yönteme çağrı çöp toplayıcısonlandırıcı çalışmasını engeller. Türün sonlandırıcısı yoksa, aramanın <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> bir etkisi yoktur. Yönetilmeyen kaynakların serbest bırakılması fiili çalışmanın `Dispose` yöntemin ikinci aşırı yükü yle gerçekleştirildiğini unutmayın.  
  
### <a name="the-disposeboolean-overload"></a>Bertaraf (Boolean) aşırı yük

İkinci aşırı yükte, *döşeyen* parametre <xref:System.Boolean> yöntem çağrısının bir <xref:System.IDisposable.Dispose%2A> yöntemden mi `true`(değeri) mi yoksa bir sonlandırıcıdan mı (değeri) geldiğini gösteren bir parametredir. `false`  
  
Yöntemin gövdesi iki kod bloğundan oluşur:  
  
- Yönetilmeyen kaynakları serbest bırakan bir blok. Bu `disposing` blok, parametrenin değerine bakılmaksızın yürütülür.  
  
- Yönetilen kaynakları serbest bırakan koşullu bir blok. `disposing` Değeri `true`. Serbest bıraktığı yönetilen kaynaklar şunları içerebilir:  
  
  **Uygulanan <xref:System.IDisposable>yönetilen nesneler.** Koşullu blok, uygulamalarını <xref:System.IDisposable.Dispose%2A> çağırmak için kullanılabilir. Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> kullandıysanız, uygulamayı buradan aramalısınız.  
  
  **Büyük miktarda bellek tüketen veya kıt kaynakları tüketen yönetilen nesneler.** `Dispose` Yöntemde bu nesneleri açıkça serbest bırakma, çöp toplayıcı tarafından deterministically geri olsaydı daha hızlı onları serbest bırakır.  
  
Yöntem çağrısı bir sonlandırıcıdan geliyorsa (yani, *atlayış* ise), `false`yalnızca yönetilmeyen kaynakları serbest bırakan kod yürütülür. Çöp toplayıcısının sonlandırma sırasında yönetilen nesneleri yok etme sırası tanımlanmadığından, bu `Dispose` aşırı `false` yüklemeyi değer değeriyle çağırmak, sonlandırıcının zaten geri alınmış olabilecek yönetilen kaynakları serbest bırakmaya çalışmasına engel olabilir.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Dispose desenini bir temel sınıf için uygulama

Dispose desenini bir temel sınıf için uygularsanız, aşağıdakileri sağlamanız gerekir:  
  
> [!IMPORTANT]
> Bu deseni uygulayan <xref:System.IDisposable.Dispose> ve olmayan `sealed` tüm temel`NotInheritable` sınıflar için (Visual Basic'te) uygulamalısınız.  
  
- Yöntemi <xref:System.IDisposable.Dispose%2A> çağıran bir `Dispose(Boolean)` uygulama.  
  
- Kaynakları `Dispose(Boolean)` serbest bırakma fiili çalışmasını gerçekleştiren bir yöntem.  
  
- Yönetilmeyen kaynağınızı <xref:System.Runtime.InteropServices.SafeHandle> saran (önerilen) bir sınıf veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yönteme geçersiz kılma. Sınıf, <xref:System.Runtime.InteropServices.SafeHandle> sizi birinci koda sahip olmaktan kurtaracak bir sonlandırıcı sağlar.  
  
Burada, güvenli bir tutamaç kullanan bir taban sınıfı için elden çıkarma deseni uygulamak için genel desen vereyim.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Önceki örnek, <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> deseni göstermek için bir nesne kullanır; türetilen <xref:System.Runtime.InteropServices.SafeHandle> herhangi bir nesne bunun yerine kullanılabilir. Örneğin nesnesini <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> düzgün bir şekilde anlık olarak açmadığını unutmayın.  
  
İşte geçersiz kılan <xref:System.Object.Finalize%2A?displayProperty=nameWithType>bir taban sınıf için elden çıkarma deseni uygulamak için genel desen.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> C#'da, bir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> [yıkıcı](../../csharp/programming-guide/classes-and-structs/destructors.md)tanımlayarak geçersiz kılınırsınız.  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Türetilen bir sınıf için dispose desenini uygulama

<xref:System.IDisposable> Arabirimi uygulayan bir sınıftan türetilen bir <xref:System.IDisposable>sınıf, taban sınıf <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması türetilmiş sınıfları tarafından devralındı, çünkü uygulamamalıdır. Bunun yerine, türetilmiş bir sınıfın kaynaklarını serbest bırakmak için aşağıdakileri sağlarsınız:  
  
- Taban `protected Dispose(Boolean)` sınıf yöntemini geçersiz kılan ve türemiş sınıfın kaynaklarını serbest bırakma fiili çalışmasını gerçekleştiren bir yöntem. Bu yöntem, taban `Dispose(Boolean)` sınıfın yöntemini de çağırmalı ve bağımsız değişken için onun disposing durumunu geçmelidir.  
  
- Yönetilmeyen kaynağınızı <xref:System.Runtime.InteropServices.SafeHandle> saran (önerilen) bir sınıf veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yönteme geçersiz kılma. Sınıf, <xref:System.Runtime.InteropServices.SafeHandle> sizi birinci koda sahip olmaktan kurtaracak bir sonlandırıcı sağlar. Bir sonlandırıcı sağlarsanız, aşırı yüklemeyi `Dispose(Boolean)` '' nin ''i `false`bir *'döşey)* bağımsız değişkeniyle aramalıdır.  
  
Güvenli tanıtıcı kullanan bir türetilen sınıf için dispose deseni uygulamada genel düzen aşağıdaki gibidir:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Önceki örnek, <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> deseni göstermek için bir nesne kullanır; türetilen <xref:System.Runtime.InteropServices.SafeHandle> herhangi bir nesne bunun yerine kullanılabilir. Örneğin nesnesini <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> düzgün bir şekilde anlık olarak açmadığını unutmayın.  
  
İşte geçersiz kılan <xref:System.Object.Finalize%2A?displayProperty=nameWithType>türemiş bir sınıf için elden çıkarma deseni uygulamak için genel desen:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> C#'da, bir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> [yıkıcı](../../csharp/programming-guide/classes-and-structs/destructors.md)tanımlayarak geçersiz kılınırsınız.  
  
<a name="SafeHandles"></a>
## <a name="using-safe-handles"></a>Güvenli tanıtıcıları kullanma

Bir nesnenin sonlandırıcısı için kod yazmak, doğru yapılmaması durumunda sorunlara neden olabilecek karmaşık bir görevdir. Bu nedenle, bir <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sonlandırıcı uygulamak yerine nesneler oluşturmanızı öneririz.  
  
<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> Sınıftan türetilen sınıflar, işletiyi kesintisiz atayarak ve serbest bırakarak nesne yaşam boyu sorunlarını basitleştirir. Uygulama etki alanı kaldırılırken çalıştırılması kesin olan kritik bir sonlandırıcı içerirler. Güvenli bir tutamaç kullanmanın avantajları hakkında <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>daha fazla bilgi için bkz. <xref:Microsoft.Win32.SafeHandles> Ad alanında aşağıdaki türetilmiş sınıflar güvenli tutamaçları sağlar:  
  
- <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>Dosyalar, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>bellek <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> eşlenen dosyalar ve borular için , ve sınıf.  
  
- Sınıf, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> bellek görünümleri için.  
  
- Şifreleme <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>yapıları <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> için , , ve sınıflar.  
  
- Sınıf, <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> kayıt anahtarları için.  
  
- Sınıf, <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> bekleme kolları için.  
  
<a name="base"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Bir temel sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnek, yönetilmeyen kaynakları kapsüllemek `DisposableStreamResource`için güvenli bir tanıtıcı kullanan bir taban sınıf için elden çıkarma deseni gösteriş gösterir. Açık bir `DisposableResource` dosyayı temsil <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> eden <xref:System.IO.Stream> bir nesneyi sarmak için a kullanan bir sınıf tanımlar. Yöntem, `DisposableResource` dosya akışındaki `Size`toplam bayt sayısını döndüren tek bir özellik de içerir.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Bir türetilen sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnek, önceki örnekte sunulan `DisposableStreamResource2` `DisposableStreamResource` sınıftan devralınan türetilmiş sınıf için elden çıkarma deseni gösteriş gösterir. Sınıf ek bir yöntem `WriteFileInfo`ekler ve <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> yazılabilir dosyanın tutamacını sarmak için bir nesne kullanır.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Sınıfları ve Yapıları Tanımlama ve Kullanma (C++/CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
- [Dispose Deseni](implementing-dispose.md)
