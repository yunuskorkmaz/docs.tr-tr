---
title: "Dispose yöntemi uygulama"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
caps.latest.revision: "44"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5a304c48a953b172cbcc3aa1c717a660298d36a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-dispose-method"></a>Dispose yöntemi uygulama

Uygulamanız bir <xref:System.IDisposable.Dispose%2A> uygulamanız tarafından kullanılan yönetilmeyen kaynakları serbest bırakmak yöntemi. .NET Atık toplayıcısının yerleştirme veya yönetilmeyen belleği serbest bırakın.  
  
Bir nesne atma desen denir bir [düzeni dispose](../../../docs/standard/design-guidelines/dispose-pattern.md), sipariş nesneyi lifetime öğesine uygular. Dispose deseni yalnızca yönetilmeyen kaynaklara erişen, dosya ve kanal tanıtıcıları, kayıt defteri tanıtıcıları, bekleme tanıtıcıları veya yönetilmeyen bellek bloğu işaretçileri gibi nesneler için kullanılır. Bunun nedeni, çöp toplayıcısının kullanılmayan yönetilen nesneleri geri kazanmada çok etkili olması, fakat yönetilmeyen nesneleri geri kazanamamasıdır.  
  
Dispose deseninin iki çeşidi vardır:  
  
* Bir güvenli tanıtıcı türü kullanan her yönetilmeyen kaynak sarmalamak (diğer bir deyişle, bir sınıfta türetilen <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). Bu durumda, uygulamanız <xref:System.IDisposable> arabirimi ve ek bir `Dispose(Boolean)` yöntemi. Bu önerilen değişim ve geçersiz kılma gerektirmeyen <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Ad alanı türetilmiş sınıfları kümesi sağlar <xref:System.Runtime.InteropServices.SafeHandle>, bu makalenin [güvenli tanıtıcıları kullanarak](#SafeHandles) bölümü. Yönetilmeyen kaynağınızın serbest bırakma için uygun bir sınıf bulamazsanız, kendi alt uygulayabilirsiniz <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Uygulamanız <xref:System.IDisposable> arabirimi ve ek bir `Dispose(Boolean)` yöntemi için ve ayrıca geçersiz <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. Geçersiz kılmanız gerekir <xref:System.Object.Finalize%2A> yönetilmeyen kaynakları if atıldı emin olmak için <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması aynı türden bir tüketici tarafından çağrılmaz. Önceki maddede açıklanan önerilen tekniği kullanırsanız <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı sizin adınıza yapar.  
  
Kaynakları her zaman uygun şekilde temizlendiğinden emin olmak için bir <xref:System.IDisposable.Dispose%2A> yöntemi olmalıdır aranabilir birden çok kez bir özel durum oluşturmadan.  
  
İçin sağlanan kod örneğinde <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> yöntemi gösterilir nasıl agresif atık toplama reclaimed nesne üyesi yürütülmeye devam ederken çalıştırmak bir sonlandırıcı neden olabilir. Çağırmak için iyi bir fikirdir <xref:System.GC.KeepAlive%2A> yöntemi bir uzun sonunda <xref:System.IDisposable.Dispose%2A> yöntemi.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() ve Dispose(Boolean)  

<xref:System.IDisposable> Arabirimi gerektiren tek bir parametresiz yöntemin kullanımı <xref:System.IDisposable.Dispose%2A>. Ancak, dispose düzeni iki gerektirir `Dispose` uygulanacak yöntemleri:  
  
* Sanal olmayan bir ortak (`NonInheritable` Visual Basic'te) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasında, hiç parametre yok.  
  
* Bir korumalı sanal (`Overridable` Visual Basic'te) `Dispose` , imza yöntemi:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose() aşırı yüklemesi

Çünkü sanal olmayan ortak (`NonInheritable` Visual Basic'te), parametresiz `Dispose` yöntemi türü bir tüketici tarafından çağrıldığında, amacı yönetilmeyen kaynakları serbest bırakmak ve biri varsa sonlandırıcıyı çalıştırmak sahip değil belirtmek için. Bu nedenle, standart bir uygulaması vardır:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` Yöntemi gerçekleştirir tüm nesne temizleme, atık toplayıcı artık nesnelerin çağırması gerekir böylece <xref:System.Object.Finalize%2A?displayProperty=nameWithType> geçersiz kılar. Bu nedenle, çağrısına <xref:System.GC.SuppressFinalize%2A> yöntemi atık toplayıcı sonlandırıcıyı çalışmasını önler. Türü çağrısı yoktur sonlandırıcıyı olup olmadığını <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> hiçbir etkisi olmaz. Yönetilmeyen kaynakları serbest bırakma, gerçek iş Not ikinci aşırı yüklemesini tarafından gerçekleştirilen `Dispose` yöntemi.  
  
### <a name="the-disposeboolean-overload"></a>Dispose(Boolean) aşırı yüklemesi

İkinci aşırı içinde *atma* parametresi bir <xref:System.Boolean> yöntem çağrısının geldiği olup olmadığını bildiren bir <xref:System.IDisposable.Dispose%2A> yöntemi (değeri olduğu `true`) veya bir sonlandırıcı (değeri olduğu `false`).  
  
Yöntemin gövdesi iki kod bloğundan oluşur:  
  
* Yönetilmeyen kaynakları serbest bırakan bir blok. Bu bloğu değeri bağımsız olarak yürütür `disposing` parametresi.  
  
* Yönetilen kaynakları serbest bırakan koşullu bir blok. Varsa bu bloğu yürütür değerini `disposing` olan `true`. Serbest bıraktığı yönetilen kaynaklar şunları içerebilir:  
  
  **Yönetilen uygulayan nesneler <xref:System.IDisposable>.** Koşullu blok çağırmak için kullanılan kendi <xref:System.IDisposable.Dispose%2A> uygulaması. Yönetilmeyen kaynağınızın sarmalamak için güvenli bir tanıtıcı kullandıysanız çağırmalıdır <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> burada uygulama.  
  
  **Büyük miktarlarda bellek kullanan veya olması kaynaklarını tüketebilir nesneleri yönetilen.** Bunlar boşaltma nesneleri açıkça içinde `Dispose` yöntemi yayımları bunları bunlar belirleyici olmayan atık toplayıcısı tarafından geri kazanılan varsa daha hızlı.  
  
Yöntem çağrısının sonlandırıcıyı geliyorsa (varsa, diğer bir deyişle, *atma* olan `false`), yalnızca yönetilmeyen kaynakları serbest bırakır kodu yürütür. İçinde atık toplayıcı bozar yönetilen nesneleri sonlandırma sırasında sipariş tanımlanmadığından, bu çağırma `Dispose` aşırı değeriyle `false` sonlandırıcıyı olabilir yönetilen kaynakları serbest bırakmak denemesini engeller zaten iadesi.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Dispose desenini bir temel sınıf için uygulama

Dispose desenini bir temel sınıf için uygularsanız, aşağıdakileri sağlamanız gerekir:  
  
> [!IMPORTANT]
> Bu deseni uygulayan tüm temel sınıflar için uygulamalıdır <xref:System.IDisposable.Dispose> ve `sealed` (`NotInheritable` Visual Basic'te).  
  
* A <xref:System.IDisposable.Dispose%2A> çağıran uygulama `Dispose(Boolean)` yöntemi.  
  
* A `Dispose(Boolean)` Kaynakları yayınlama asıl işi yapan yöntemi.  
  
* Her iki sınıfın türetildiği <xref:System.Runtime.InteropServices.SafeHandle> Yönetilmeyen kaynağınızın (önerilen) veya bir geçersiz kılma sarmalar <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. <xref:System.Runtime.InteropServices.SafeHandle> Sınıfı, kodu bir kalmaktan boşaltır sonlandırıcıyı sağlar.  
  
Burada, güvenli bir tanıtıcı kullanan bir taban sınıfı için dispose desen uygulamak için genel düzeni verilmiştir.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Önceki örnekte kullanan bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> düzeni göstermek için nesne; herhangi bir nesne türetilmiş <xref:System.Runtime.InteropServices.SafeHandle> yerine kullanılabilir. Örnek değil düzgün örneği Not kendi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesi.  
  
Geçersiz kılan bir taban sınıfı için dispose desen uygulamak için genel düzeni işte <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> C# ' ta kılmanız <xref:System.Object.Finalize%2A?displayProperty=nameWithType> tanımlayarak bir [yıkıcı](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Türetilen bir sınıf için dispose desenini uygulama

Arabirimini uygulayan bir sınıftan türetilmiş bir sınıf <xref:System.IDisposable> döndürmemelidir arabirimini uygulayan <xref:System.IDisposable>, temel sınıf çünkü uyarlamasını <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> kendi türetilen sınıflar tarafından devralınır. Onun yerine, türetilen bir sınıfa ilişkin olarak dispose desenini uygulamak için aşağıdakileri sağlarsınız:  
  
* A `protected``Dispose(Boolean)` temel sınıf yöntemini geçersiz kılar ve türetilmiş sınıf Kaynakları yayınlama gerçek iş gerçekleştiren yöntemi. Bu yöntem de çağırmanız gerekir `Dispose(Boolean)` yöntemi taban sınıf ve değerini geçirin `true` için *atma* bağımsız değişkeni.  
  
* Her iki sınıfın türetildiği <xref:System.Runtime.InteropServices.SafeHandle> Yönetilmeyen kaynağınızın (önerilen) veya bir geçersiz kılma sarmalar <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. <xref:System.Runtime.InteropServices.SafeHandle> Sınıfı, kodu bir kalmaktan boşaltır sonlandırıcıyı sağlar. Bir sonlandırıcı sağlarsanız, çağırmalıdır `Dispose(Boolean)` ile aşırı bir *atma* bağımsız değişkeni `false`.  
  
Güvenli tanıtıcı kullanan bir türetilen sınıf için dispose deseni uygulamada genel düzen aşağıdaki gibidir:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Önceki örnekte kullanan bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> düzeni göstermek için nesne; herhangi bir nesne türetilmiş <xref:System.Runtime.InteropServices.SafeHandle> yerine kullanılabilir. Örnek değil düzgün örneği Not kendi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesnesi.  
  
Geçersiz kılmaları türetilmiş bir sınıf için dispose desen uygulamak için genel düzeni işte <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> C# ' ta kılmanız <xref:System.Object.Finalize%2A?displayProperty=nameWithType> tanımlayarak bir [yıkıcı](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Güvenli tanıtıcıları kullanma

Bir nesnenin sonlandırıcısı için kod yazmak, doğru yapılmaması durumunda sorunlara neden olabilecek karmaşık bir görevdir. Bu nedenle, oluşturmak öneririz <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> bir sonlandırıcı uygulamak yerine nesneleri.  
  
Türetilmiş sınıflar <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı atayarak ve kesintisiz işleyicilerini serbest nesne ömrü sorunları basitleştirin. Uygulama etki alanı kaldırılırken çalıştırılması kesin olan kritik bir sonlandırıcı içerirler. Güvenli bir işleci kullanılarak avantajları hakkında daha fazla bilgi için bkz: <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Aşağıdaki sınıflar türetilmiş <xref:Microsoft.Win32.SafeHandles> ad alanı güvenli tanıtıcıları sağlayın:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, Ve <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> dosyaları, bellekle eşlenen dosyalar ve kanallar için sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Bellek görünümleri için sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, Ve <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> şifreleme yapıları için sınıflar.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Kayıt defteri anahtarları için sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Bekleme tanıtıcıları için sınıf.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Bir temel sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnekte, bir taban sınıfı için dispose deseni gösterilmektedir `DisposableStreamResource`kullanan bir güvenli işlemek, yönetilmeyen kaynakları için. Bunu tanımlayan bir `DisposableResource` kullanan sınıfı bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> sarmalamak için bir <xref:System.IO.Stream> açık bir dosyayı temsil eden nesne. `DisposableResource` Yöntemi de tek bir özellik içerir `Size`, toplam bayt sayısı dosya akışında getirir.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Bir türetilen sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnekte, türetilmiş bir sınıf için dispose deseni gösterilmektedir `DisposableStreamResource2`, devraldığı `DisposableStreamResource` önceki örnekte sunulan sınıfı. Ek bir yöntem sınıfı ekler `WriteFileInfo`ve kullandığı bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> yazılabilir bir dosya tanıtıcısı sarmalamak için nesne.  
  
[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

<xref:System.GC.SuppressFinalize%2A>   
<xref:System.IDisposable>   
<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>   
<xref:Microsoft.Win32.SafeHandles>   
<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>   
<xref:System.Object.Finalize%2A?displayProperty=nameWithType>   
[Nasıl yapılır: sınıfları ve yapıları tanımlama ve kullanma (C + +/ CLI)](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)   
[Desen dispose](../../../docs/standard/design-guidelines/dispose-pattern.md)
