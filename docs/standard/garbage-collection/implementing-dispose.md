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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2881ef5b4cbc5850fde64fc68640021ebf42df43
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666459"
---
# <a name="implementing-a-dispose-method"></a>Dispose yöntemi uygulama

Uygulamanız tarafından kullanılan <xref:System.IDisposable.Dispose%2A> yönetilmeyen kaynakları serbest bırakmak için bir yöntem uygulayın. .NET atık toplayıcısı, yönetilmeyen bellek ayırır veya serbest bırakmaz.  
  
[Dispose düzeni](../../../docs/standard/design-guidelines/dispose-pattern.md)olarak adlandırılan bir nesneyi elden atma düzeni, bir nesnenin ömrüne göre sıra uygular. Dispose deseni yalnızca yönetilmeyen kaynaklara erişen, dosya ve kanal tanıtıcıları, kayıt defteri tanıtıcıları, bekleme tanıtıcıları veya yönetilmeyen bellek bloğu işaretçileri gibi nesneler için kullanılır. Bunun nedeni, çöp toplayıcısının kullanılmayan yönetilen nesneleri geri kazanmada çok etkili olması, fakat yönetilmeyen nesneleri geri kazanamamasıdır.  
  
Dispose deseninin iki çeşidi vardır:  
  
* Bir türün kullandığı her yönetilmeyen kaynağı güvenli bir tanıtıcı (yani, öğesinden <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>türetilmiş bir sınıfta) sarın. Bu durumda, <xref:System.IDisposable> arabirimini ve ek `Dispose(Boolean)` bir yöntemi uygulacağınızı görürsünüz. Bu önerilen çeşitdir ve <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi geçersiz kılmayı gerektirmez.  
  
  > [!NOTE]
  > Ad alanı, [güvenli işleyiciler kullanılarak](#SafeHandles) listelenen öğesinden <xref:System.Runtime.InteropServices.SafeHandle>türetilmiş bir sınıf kümesi sağlar. <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Yönetilmeyen kaynağınız serbest bırakmak için uygun bir sınıf bulamıyorsanız, kendi alt <xref:System.Runtime.InteropServices.SafeHandle>sınıfınızı uygulayabilirsiniz.  
  
* <xref:System.IDisposable> Arabirimini ve ek `Dispose(Boolean)` bir yöntemi uygularsınız ve ayrıca <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemini geçersiz kılarsınız. Uygulamanız sizin <xref:System.Object.Finalize%2A> <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bir tüketici tarafından çağrılmadığı takdirde yönetilmeyen kaynakların çıkarıldığından emin olmak için geçersiz kılmanız gerekir. Önceki madde işaretinde açıklanan önerilen tekniği kullanırsanız, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı bunu sizin yerinize yapar.  
  
Kaynakların her zaman uygun şekilde temizlendiğinden emin olmak için bir <xref:System.IDisposable.Dispose%2A> Yöntem özel durum oluşturmadan birden çok kez çağrılabilir olmalıdır.  
  
<xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> Yöntemi için belirtilen kod örneği, ısrarlı çöp toplamanın, geri kazanılan nesnenin bir üyesi hala yürütülürken sonlandırıcının çalışmasına nasıl neden olabileceği gösterilmektedir. <xref:System.GC.KeepAlive%2A> Yöntemi uzun<xref:System.IDisposable.Dispose%2A> bir yöntemin sonunda çağırmak iyi bir fikirdir.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() ve Dispose(Boolean)  

Arabirim, tek parametresiz bir <xref:System.IDisposable.Dispose%2A>yöntemin uygulanmasını gerektirir. <xref:System.IDisposable> Ancak, Dispose deseninin uygulanması için iki `Dispose` yöntem gerekir:  
  
* Parametresi olmayan, ortak sanal olmayan`NonInheritable` (Visual Basic) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> bir uygulama.  
  
* İmzası şu olan korumalı`Overridable` bir sanal ( `Dispose` Visual Basic) yöntemi:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose () aşırı yüklemesi

Ortak, sanal olmayan (`NonInheritable` Visual Basic), parametresiz `Dispose` Yöntem türünün bir tüketicisi tarafından çağrıldığı için, amacı yönetilmeyen kaynakları serbest bırakmak ve varsa sonlandırıcının çalıştırmak zorunda olmadığını gösterir. Bu nedenle, standart bir uygulaması vardır:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
Yöntemi tüm nesne temizleme işlemini gerçekleştirir, bu nedenle çöp toplayıcının artık <xref:System.Object.Finalize%2A?displayProperty=nameWithType> nesnelerin geçersiz kılmasını çağırması gerekmez. `Dispose` Bu nedenle, <xref:System.GC.SuppressFinalize%2A> yöntemine yapılan çağrı çöp toplayıcısının sonlandırıcıyı çalıştırmasını önler. Türün Sonlandırıcı yoksa, çağrısının <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> hiçbir etkisi olmaz. Yönetilmeyen kaynakları serbest bırakan gerçek çalışmanın, `Dispose` yöntemin ikinci aşırı yüklemesi tarafından gerçekleştirildiğini unutmayın.  
  
### <a name="the-disposeboolean-overload"></a>Dispose (Boolean) aşırı yüklemesi

İkinci aşırı yükte, *disposing* parametresi, yöntem çağrısının <xref:System.Boolean> bir <xref:System.IDisposable.Dispose%2A> yöntemden (değer `true`) mi yoksa sonlandırıcının mi (değer `false`) geldiğini belirten bir değeridir.  
  
Yöntemin gövdesi iki kod bloğundan oluşur:  
  
* Yönetilmeyen kaynakları serbest bırakan bir blok. Bu blok, `disposing` parametrenin değerinden bağımsız olarak yürütülür.  
  
* Yönetilen kaynakları serbest bırakan koşullu bir blok. Değeri `disposing` ise`true`bu blok yürütülür. Serbest bıraktığı yönetilen kaynaklar şunları içerebilir:  
  
  **Uygulayan <xref:System.IDisposable>yönetilen nesneler.** Koşullu blok, <xref:System.IDisposable.Dispose%2A> uygulamasını çağırmak için kullanılabilir. Yönetilmeyen kaynağınızı kaydırmak için güvenli bir tanıtıcı kullandıysanız, <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> uygulamayı buradan çağırmanız gerekir.  
  
  **Büyük miktarlarda bellek kullanan veya nadir kaynaklarını tüketen yönetilen nesneler.** Bu nesneleri açıkça `Dispose` serbest bırakma, çöp toplayıcı tarafından belirleyici olmayan şekilde geri kazanıladıklarından daha hızlı bir şekilde serbest bırakır.  
  
Yöntem çağrısı bir sonlandırıcının geliyorsa (yani, *disposing* `false`ise), yalnızca yönetilmeyen kaynakları serbest bırakma kodu yürütülür. Çöp toplayıcı 'nın `Dispose` `false` sonlandırma sırasında yönetilen nesneleri yok ettiği sıra tanımlanmadığı için, bu aşırı yüklemeyi bir değeriyle çağırmak, sonlandırıcının sahip olabilecek yönetilen kaynakları serbest bırakmaya çalışmasını önler zaten kazanıldı.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Dispose desenini bir temel sınıf için uygulama

Dispose desenini bir temel sınıf için uygularsanız, aşağıdakileri sağlamanız gerekir:  
  
> [!IMPORTANT]
> Bu kalıbı, uygulayan <xref:System.IDisposable.Dispose> ve olmayan `sealed` (`NotInheritable` Visual Basic) tüm temel sınıflar için uygulamalısınız.  
  
* Yöntemini çağıran bir <xref:System.IDisposable.Dispose%2A>uygulama. `Dispose(Boolean)`  
  
* Kaynak `Dispose(Boolean)` bırakma işinin gerçek işini gerçekleştiren bir yöntem.  
  
* Öğesinden <xref:System.Runtime.InteropServices.SafeHandle> türetilen bir sınıf, Yönetilmeyen kaynağınızı sarmalanmış (önerilir) veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemine bir geçersiz kılma. <xref:System.Runtime.InteropServices.SafeHandle> Sınıfı, sizi kod içine almak zorunda kalmanızı sağlayan bir Sonlandırıcı sağlar.  
  
Aşağıda, güvenli tanıtıcı kullanan bir temel sınıf için Dispose deseninin uygulanması için genel bir model verilmiştir.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Önceki örnek, bir nesneyi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> göstermek için bir nesnesi kullanır; bunun yerine <xref:System.Runtime.InteropServices.SafeHandle> ondan türetilmiş herhangi bir nesne kullanılabilir. Örneğin <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesinin düzgün şekilde örneklemez olduğunu unutmayın.  
  
Geçersiz kılan <xref:System.Object.Finalize%2A?displayProperty=nameWithType>bir temel sınıf için Dispose deseninin uygulanması için genel bir model.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> İçinde C#, bir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> [yıkıcı](../../csharp/programming-guide/classes-and-structs/destructors.md)tanımlayarak geçersiz kılabilirsiniz.  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Türetilen bir sınıf için dispose desenini uygulama

Temel sınıf uygulaması <xref:System.IDisposable> <xref:System.IDisposable> türetilmişsınıflarıtarafındandevralındığından,arabiriminiuygulayanbirsınıftantüretilmişbir<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sınıf uygulanmamalıdır. Onun yerine, türetilen bir sınıfa ilişkin olarak dispose desenini uygulamak için aşağıdakileri sağlarsınız:  
  
* Temel `protected Dispose(Boolean)` sınıf yöntemini geçersiz kılan ve türetilen sınıfın kaynaklarını serbest bırakma işinin asıl işini gerçekleştiren bir yöntem. Bu yöntem ayrıca temel sınıfın `Dispose(Boolean)` yöntemini çağırmalıdır ve bağımsız değişkeni için disposing durumunu iletmelidir.  
  
* Öğesinden <xref:System.Runtime.InteropServices.SafeHandle> türetilen bir sınıf, Yönetilmeyen kaynağınızı sarmalanmış (önerilir) veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemine bir geçersiz kılma. <xref:System.Runtime.InteropServices.SafeHandle> Sınıfı, sizi kod içine almak zorunda kalmanızı sağlayan bir Sonlandırıcı sağlar. Bir Sonlandırıcı sağlarsanız,, öğesinin `Dispose(Boolean)` `false`bir *disposing* bağımsız değişkeniyle birlikte aşırı yüklemeyi çağırmalıdır.  
  
Güvenli tanıtıcı kullanan bir türetilen sınıf için dispose deseni uygulamada genel düzen aşağıdaki gibidir:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Önceki örnek, bir nesneyi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> göstermek için bir nesnesi kullanır; bunun yerine <xref:System.Runtime.InteropServices.SafeHandle> ondan türetilmiş herhangi bir nesne kullanılabilir. Örneğin <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesinin düzgün şekilde örneklemez olduğunu unutmayın.  
  
Geçersiz kılan <xref:System.Object.Finalize%2A?displayProperty=nameWithType>türetilmiş bir sınıf için Dispose deseninin uygulanması için genel bir model aşağıda verilmiştir:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> İçinde C#, bir <xref:System.Object.Finalize%2A?displayProperty=nameWithType> [yıkıcı](../../csharp/programming-guide/classes-and-structs/destructors.md)tanımlayarak geçersiz kılabilirsiniz.  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Güvenli tanıtıcıları kullanma

Bir nesnenin sonlandırıcısı için kod yazmak, doğru yapılmaması durumunda sorunlara neden olabilecek karmaşık bir görevdir. Bu nedenle, bir Sonlandırıcı uygulamak yerine <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> nesneleri oluşturmanızı öneririz.  
  
Sınıfından türetilmiş sınıflar, <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> kesintiye uğramadan işleyicileri atayarak ve serbest bırakarak nesne ömrü sorunlarını basitleştirir. Uygulama etki alanı kaldırılırken çalıştırılması kesin olan kritik bir sonlandırıcı içerirler. Güvenli bir tanıtıcı kullanmanın avantajları hakkında daha fazla bilgi için bkz <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. <xref:Microsoft.Win32.SafeHandles> Ad alanındaki aşağıdaki türetilmiş sınıflar, güvenli işleyiciler sağlar:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, ,<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>Ve sınıfı,dosyalar<xref:Microsoft.Win32.SafeHandles.SafePipeHandle> , bellek eşlemeli dosyalar ve kanallar için.  
  
* Bellek görünümleri için sınıfı. <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>  
  
* Şifreleme yapıları için, <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> ve sınıfları. <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle> <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>  
  
* Kayıt defteri anahtarları için sınıfı.<xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle>  
  
* Wait tutamaçları için sınıfı. <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Bir temel sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnek, yönetilmeyen kaynakları kapsüllemek için güvenli bir tanıtıcı kullanan `DisposableStreamResource`bir temel sınıf için Dispose modelini göstermektedir. Açık bir dosyayı `DisposableResource` temsil eden bir <xref:System.IO.Stream> nesneyi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> kaydırmak için öğesini kullanan bir sınıfı tanımlar. Yöntemi, dosya akışındaki toplam bayt sayısını döndüren `Size`tek bir özelliğini de içerir. `DisposableResource`  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Bir türetilen sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnek, önceki örnekte sunulan `DisposableStreamResource2` `DisposableStreamResource` sınıftan devralan türetilmiş bir sınıf için Dispose modelini göstermektedir. Sınıfı ek bir yöntemi `WriteFileInfo`ekler, ve yazılabilir dosyanın tanıtıcısını kaydırmak için bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesi kullanır.  
  
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
