---
title: Dispose yöntemi uygulama
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: 8a29584dd5ed47ad1e8a336a7283cba9271f3abd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121204"
---
# <a name="implementing-a-dispose-method"></a>Dispose yöntemi uygulama

Uygulamanız tarafından kullanılan yönetilmeyen kaynakları serbest bırakmak için bir <xref:System.IDisposable.Dispose%2A> yöntemi uygulamanız gerekir. .NET atık toplayıcısı, yönetilmeyen bellek ayırır veya serbest bırakmaz.  
  
[Dispose düzeni](../../../docs/standard/design-guidelines/dispose-pattern.md)olarak adlandırılan bir nesneyi elden atma düzeni, bir nesnenin ömrüne göre sıra uygular. Dispose deseni yalnızca yönetilmeyen kaynaklara erişen, dosya ve kanal tanıtıcıları, kayıt defteri tanıtıcıları, bekleme tanıtıcıları veya yönetilmeyen bellek bloğu işaretçileri gibi nesneler için kullanılır. Bunun nedeni, çöp toplayıcısının kullanılmayan yönetilen nesneleri geri kazanmada çok etkili olması, fakat yönetilmeyen nesneleri geri kazanamamasıdır.  
  
Dispose deseninin iki çeşidi vardır:  
  
- Bir türün kullandığı her yönetilmeyen kaynağı bir güvenli tanıtıcıda (yani <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>türetilmiş bir sınıfta) sarın. Bu durumda, <xref:System.IDisposable> arabirimini ve ek bir `Dispose(Boolean)` yöntemini uygulayacağınızı görürsünüz. Bu önerilen çeşitdir ve <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi geçersiz kılmayı gerektirmez.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> ad alanı, [güvenli Işleyiciler kullanma](#SafeHandles) bölümünde listelenen <xref:System.Runtime.InteropServices.SafeHandle>türetilmiş bir sınıf kümesi sağlar. Yönetilmeyen kaynağınız serbest bırakmak için uygun bir sınıf bulamıyorsanız, kendi <xref:System.Runtime.InteropServices.SafeHandle>kendi alt sınıfınızı uygulayabilirsiniz.  
  
- <xref:System.IDisposable> arabirimini ve ek bir `Dispose(Boolean)` yöntemini uygularsınız ve ayrıca <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemini geçersiz kılarsınız. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamanız, türden bir tüketici tarafından çağrılmadığı takdirde yönetilmeyen kaynakların ' ın çıkarıldığından emin olmak için <xref:System.Object.Finalize%2A> geçersiz kılmanız gerekir. Önceki madde işaretinde ele alınan önerilen tekniği kullanırsanız <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı bunu sizin yerinize yapar.  
  
Kaynakların her zaman uygun şekilde temizlendiğinden emin olmak için bir <xref:System.IDisposable.Dispose%2A> yöntemi özel durum oluşturmadan birden çok kez çağrılabilir olmalıdır.  
  
<xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> yöntemi için belirtilen kod örneği, ısrarlı çöp toplamanın, geri kazanılan nesnenin bir üyesi hala yürütülürken sonlandırıcının çalışmasına nasıl neden olabileceği gösterilmektedir. Uzun bir <xref:System.IDisposable.Dispose%2A> yönteminin sonunda <xref:System.GC.KeepAlive%2A> yöntemini çağırmak iyi bir fikirdir.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() ve Dispose(Boolean)  

<xref:System.IDisposable> arabirimi, <xref:System.IDisposable.Dispose%2A>tek bir parametresiz yöntemin uygulanmasını gerektirir. Ancak, Dispose deseninin uygulanması için iki `Dispose` yöntemi gerekir:  
  
- Bir parametre içermeyen, uygulama <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> ortak sanal olmayan bir (Visual Basic`NonInheritable`).  
  
- İmzaya sahip korumalı bir sanal (Visual Basic`Overridable`) `Dispose` yöntemi:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose () aşırı yüklemesi

Ortak, sanal olmayan (Visual Basic`NonInheritable`), parametresiz `Dispose` yöntemi türü bir tüketici tarafından çağrıldığından amacı, yönetilmeyen kaynakları serbest bırakmak ve varsa sonlandırıcının çalıştırması gerekmez. Bu nedenle, standart bir uygulaması vardır:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` yöntemi tüm nesne temizleme işlemini gerçekleştirir, bu nedenle çöp toplayıcının artık ' <xref:System.Object.Finalize%2A?displayProperty=nameWithType> override ' nesnelerini çağırması gerekmez. Bu nedenle, <xref:System.GC.SuppressFinalize%2A> yöntemine yapılan çağrı, çöp toplayıcısının sonlandırıcıyı çalıştırmasını önler. Türün sonlandırıcısı yoksa <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> çağrısının hiçbir etkisi olmaz. Yönetilmeyen kaynakları serbest bırakma işinin gerçek işinin `Dispose` yönteminin ikinci aşırı yüklemesi tarafından gerçekleştirildiğini unutmayın.  
  
### <a name="the-disposeboolean-overload"></a>Dispose (Boolean) aşırı yüklemesi

İkinci aşırı yüklemede, *disposing* parametresi, yöntem çağrısının bir <xref:System.IDisposable.Dispose%2A> yönteminden (değer `true`) mi yoksa sonlandırıcının mi (değer `false`) geldiğini belirten bir <xref:System.Boolean>.  
  
Yöntemin gövdesi iki kod bloğundan oluşur:  
  
- Yönetilmeyen kaynakları serbest bırakan bir blok. Bu blok `disposing` parametresinin değerinden bağımsız olarak yürütülür.  
  
- Yönetilen kaynakları serbest bırakan koşullu bir blok. `disposing` değeri `true`ise bu blok yürütülür. Serbest bıraktığı yönetilen kaynaklar şunları içerebilir:  
  
  **<xref:System.IDisposable>uygulayan yönetilen nesneler.** Koşullu blok, <xref:System.IDisposable.Dispose%2A> uygulamasını çağırmak için kullanılabilir. Yönetilmeyen kaynağınızı kaydırmak için güvenli bir tanıtıcı kullandıysanız buradaki <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> uygulamasını çağırmanız gerekir.  
  
  **Büyük miktarlarda bellek kullanan veya nadir kaynaklarını tüketen yönetilen nesneler.** Bu nesneleri açıkça `Dispose` yönteminde serbest bırakma, çöp toplayıcı tarafından belirleyici olmayan şekilde geri kazanıladıklarından daha hızlı bir şekilde serbest bırakır.  
  
Yöntem çağrısı bir sonlandırıcının geliyorsa (yani, *disposing* `false`), yalnızca yönetilmeyen kaynakları serbest bırakma kodu yürütülür. Çöp toplayıcı 'nın sonlandırma sırasında yönetilen nesneleri yok ettiği sıra tanımlanmadığı için, bu `Dispose` aşırı yüklemesini `false` bir değer ile çağırmak, sonlandırıcının zaten yapılmış olabilecek yönetilen kaynakları serbest bırakmasına engel olur lamıyor.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Dispose desenini bir temel sınıf için uygulama

Dispose desenini bir temel sınıf için uygularsanız, aşağıdakileri sağlamanız gerekir:  
  
> [!IMPORTANT]
> Bu kalıbı <xref:System.IDisposable.Dispose> uygulayan ve `sealed` olmayan (Visual Basic`NotInheritable`) tüm temel sınıflar için uygulamalısınız.  
  
- `Dispose(Boolean)` yöntemini çağıran <xref:System.IDisposable.Dispose%2A> uygulama.  
  
- Kaynak bırakma işinin gerçek işini gerçekleştiren bir `Dispose(Boolean)` yöntemi.  
  
- Yönetilmeyen kaynağı sarmalayan <xref:System.Runtime.InteropServices.SafeHandle> türetilen bir sınıf (önerilir) veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemine bir geçersiz kılma. <xref:System.Runtime.InteropServices.SafeHandle> sınıfı, sizi kod içine almak zorunda kalmanızı sağlayan bir Sonlandırıcı sağlar.  
  
Aşağıda, güvenli tanıtıcı kullanan bir temel sınıf için Dispose deseninin uygulanması için genel bir model verilmiştir.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Önceki örnek, bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesneyi kullanarak, kalıbı gösterir; <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş herhangi bir nesne bunun yerine kullanılabilir. Örneğin <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesinin düzgün şekilde örneklemez olduğunu unutmayın.  
  
<xref:System.Object.Finalize%2A?displayProperty=nameWithType>geçersiz kılan bir temel sınıf için Dispose deseninin uygulanması için genel bir örüntü.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> İçinde C#, bir [yıkıcı](../../csharp/programming-guide/classes-and-structs/destructors.md)tanımlayarak <xref:System.Object.Finalize%2A?displayProperty=nameWithType> geçersiz kılabilirsiniz.  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Türetilen bir sınıf için dispose desenini uygulama

<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> temel sınıf uygulaması türetilmiş sınıfları tarafından devralındığından, <xref:System.IDisposable> arabirimini uygulayan bir sınıftan türetilmiş bir sınıf <xref:System.IDisposable>uygulamalıdır. Onun yerine, türetilen bir sınıfa ilişkin olarak dispose desenini uygulamak için aşağıdakileri sağlarsınız:  
  
- Temel sınıf yöntemini geçersiz kılan ve türetilen sınıfın kaynaklarını serbest bırakma işinin asıl işini gerçekleştiren bir `protected Dispose(Boolean)` yöntemi. Bu yöntem ayrıca temel sınıfın `Dispose(Boolean)` yöntemini çağırmalıdır ve bağımsız değişkeni için disposing durumunu iletmelidir.  
  
- Yönetilmeyen kaynağı sarmalayan <xref:System.Runtime.InteropServices.SafeHandle> türetilen bir sınıf (önerilir) veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemine bir geçersiz kılma. <xref:System.Runtime.InteropServices.SafeHandle> sınıfı, sizi kod içine almak zorunda kalmanızı sağlayan bir Sonlandırıcı sağlar. Bir Sonlandırıcı sağlarsanız, `false`bir *disposing* bağımsız değişkeniyle `Dispose(Boolean)` aşırı yüklemeyi çağırmalıdır.  
  
Güvenli tanıtıcı kullanan bir türetilen sınıf için dispose deseni uygulamada genel düzen aşağıdaki gibidir:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Önceki örnek, bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesneyi kullanarak, kalıbı gösterir; <xref:System.Runtime.InteropServices.SafeHandle> türetilmiş herhangi bir nesne bunun yerine kullanılabilir. Örneğin <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesinin düzgün şekilde örneklemez olduğunu unutmayın.  
  
<xref:System.Object.Finalize%2A?displayProperty=nameWithType>geçersiz kılan türetilmiş bir sınıf için Dispose deseninin uygulanması için genel bir örüntü:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> İçinde C#, bir [yıkıcı](../../csharp/programming-guide/classes-and-structs/destructors.md)tanımlayarak <xref:System.Object.Finalize%2A?displayProperty=nameWithType> geçersiz kılabilirsiniz.  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Güvenli tanıtıcıları kullanma

Bir nesnenin sonlandırıcısı için kod yazmak, doğru yapılmaması durumunda sorunlara neden olabilecek karmaşık bir görevdir. Bu nedenle, bir sonlandırıcıyı uygulamak yerine <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> nesneleri oluşturmanızı öneririz.  
  
<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfından türetilmiş sınıflar, kesintiye uğramadan işleyicileri atayarak ve serbest bırakarak nesne ömrü sorunlarını basitleştirir. Uygulama etki alanı kaldırılırken çalıştırılması kesin olan kritik bir sonlandırıcı içerirler. Güvenli bir tanıtıcı kullanmanın avantajları hakkında daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. <xref:Microsoft.Win32.SafeHandles> ad alanındaki aşağıdaki türetilmiş sınıflar, güvenli işleyiciler sağlar:  
  
- Dosyalar, bellek eşlemeli dosyalar ve kanallar için <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>ve <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> sınıfı.  
  
- Bellek görünümleri için <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> sınıfı.  
  
- Şifreleme yapıları için <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>ve <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> sınıfları.  
  
- Kayıt defteri anahtarları için <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> sınıfı.  
  
- Wait tutamaçları için <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> sınıfı.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Bir temel sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnek, yönetilmeyen kaynakları kapsüllemek için güvenli bir tanıtıcı kullanan `DisposableStreamResource`bir temel sınıf için Dispose modelini gösterir. Açık bir dosyayı temsil eden bir <xref:System.IO.Stream> nesnesini kaydırmak için <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> kullanan bir `DisposableResource` sınıfını tanımlar. `DisposableResource` yöntemi, dosya akışındaki toplam bayt sayısını döndüren `Size`tek bir özelliğini de içerir.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Bir türetilen sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnek, bir önceki örnekte sunulan `DisposableStreamResource` sınıfından devralan `DisposableStreamResource2`türetilmiş bir sınıf için Dispose modelini gösterir. Sınıfı, `WriteFileInfo`ek bir yöntem ekler ve yazılabilir dosyanın tanıtıcısını kaydırmak için bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesi kullanır.  
  
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
- [Dispose Deseni](../../../docs/standard/design-guidelines/dispose-pattern.md)
