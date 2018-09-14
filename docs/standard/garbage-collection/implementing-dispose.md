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
ms.openlocfilehash: 36526da1fc678e933a75e19bac9c8e1d0a40909c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597777"
---
# <a name="implementing-a-dispose-method"></a>Dispose yöntemi uygulama

Uygulamanız bir <xref:System.IDisposable.Dispose%2A> uygulamanız tarafından kullanılan yönetilmeyen kaynakları serbest bırakmak için yöntemi. .NET Atık toplayıcısının ayırmak veya yönetilmeyen bellek desteklemez.  
  
Olarak adlandırılan desen disposing bir nesne için bir [dispose deseni](../../../docs/standard/design-guidelines/dispose-pattern.md), bir nesnenin ömrünü üzerinde sırası uygular. Dispose deseni yalnızca yönetilmeyen kaynaklara erişen, dosya ve kanal tanıtıcıları, kayıt defteri tanıtıcıları, bekleme tanıtıcıları veya yönetilmeyen bellek bloğu işaretçileri gibi nesneler için kullanılır. Bunun nedeni, çöp toplayıcısının kullanılmayan yönetilen nesneleri geri kazanmada çok etkili olması, fakat yönetilmeyen nesneleri geri kazanamamasıdır.  
  
Dispose deseninin iki çeşidi vardır:  
  
* Bir tür güvenli bir tanıtıcıda kullandığı her bir yönetilmeyen kaynağı sararsınız (yani sınıfından türetilen bir sınıfta <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>). Bu durumda, uygulamanız <xref:System.IDisposable> arabirimini ve ek `Dispose(Boolean)` yöntemi. Bu önerilen çeşittir ve geçersiz kılınmasını gerektirmez <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi.  
  
  > [!NOTE]
  > <xref:Microsoft.Win32.SafeHandles?displayProperty=nameWithType> Ad alanı, türetilen sınıf kümesi sağlar <xref:System.Runtime.InteropServices.SafeHandle>, bu makalenin [güvenli tanıtıcıları kullanma](#SafeHandles) bölümü. Yönetilmeyen kaynağınızı serbest için uygun bir sınıf bulamazsanız, kendi alt uygulayabileceğiniz <xref:System.Runtime.InteropServices.SafeHandle>.  
  
* Uygulamanız <xref:System.IDisposable> arabirimini ve ek `Dispose(Boolean)` yöntemi ve ayrıca geçersiz <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. Geçersiz kılmanız gerekir <xref:System.Object.Finalize%2A> durumunda yönetilmeyen kaynakların elden çıkarılmasını sağlamak için <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> sizin türünüzün bir tüketicisi tarafından çağrılmaması. Önceki madde işaretinde açıklanan önerilen tekniği kullanırsanız <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı bunu sizin adınıza yapar.  
  
Kaynakların her zaman uygun şekilde temizlenmesini sağlamaya yardımcı olmak için bir <xref:System.IDisposable.Dispose%2A> yöntemi çağrılabilir olması gerekir birden çok kez bir özel durum olmadan.  
  
İçin sağlanan kod örneği <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> yöntemi gösterir nasıl katı kurallarla yapılan çöp toplama, bir sonlandırıcının geri kazanılan nesnenin bir üyesi hala Yürütülüyor iken çalışmasına neden olabilir. Çağırmak için iyi bir fikirdir <xref:System.GC.KeepAlive%2A> sonunda, uzun bir yöntem <xref:System.IDisposable.Dispose%2A> yöntemi.  
  
<a name="Dispose2"></a>
## <a name="dispose-and-disposeboolean"></a>Dispose() ve Dispose(Boolean)  

<xref:System.IDisposable> Arabirimi tek bir parametresiz yöntemin uygulanmasını gerektirir <xref:System.IDisposable.Dispose%2A>. Ancak, dispose deseni iki gerektirir `Dispose` uygulanacak yöntemleri:  
  
* Sanal olmayan bir ortak (`NonInheritable` Visual Basic'te) <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasında, hiç parametre yok.  
  
* Korunan sanal (`Overridable` Visual Basic'te) `Dispose` imzaya sahip, yöntemi:  
  
  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose() aşırı yükleme

Çünkü ortak, sanal olmayan (`NonInheritable` Visual Basic'te), parametresiz `Dispose` yöntemi, türün bir tüketicisi tarafından çağrıldığında, amacı yönetilmeyen kaynakları serbest bırakmak ve biri varsa sonlandırıcının çalıştırmak sahip olmadığını göstermek için. Bu nedenle, standart bir uygulaması vardır:  
  
[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
`Dispose` Yöntemi tüm nesne temizlemesi, çöp toplayıcı nesnelerin artık gerekir. gerçekleştirdiğinden <xref:System.Object.Finalize%2A?displayProperty=nameWithType> geçersiz kılar. Bu nedenle, çağrı <xref:System.GC.SuppressFinalize%2A> yöntemi çöp toplayıcının sonlandırıcıyı çalıştırmasını önler. Türün Sonlandırıcısı, çağrı varsa <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> hiçbir etkisi olmaz. İkinci aşırı yüklemesi tarafından gerçekleştirildiğini unutmayın yönetilmeyen kaynakları serbest bırakma işini `Dispose` yöntemi.  
  
### <a name="the-disposeboolean-overload"></a>Dispose(Boolean) aşırı yükleme

İkinci aşırı yükleme, *disposing* parametresi bir <xref:System.Boolean> yöntemi çağrısının bildiren bir <xref:System.IDisposable.Dispose%2A> yöntemi (değeri `true`) veya bir sonlandırıcıdan (değeri `false`).  
  
Yöntemin gövdesi iki kod bloğundan oluşur:  
  
* Yönetilmeyen kaynakları serbest bırakan bir blok. Bu bloğu değerine bakılmaksızın yürütülür `disposing` parametresi.  
  
* Yönetilen kaynakları serbest bırakan koşullu bir blok. Bu bloğu ise yürütülür değerini `disposing` olduğu `true`. Serbest bıraktığı yönetilen kaynaklar şunları içerebilir:  
  
  **Uygulayan yönetilen <xref:System.IDisposable>.** Koşullu blok çağırmak için kullanılabilecek kendi <xref:System.IDisposable.Dispose%2A> uygulaması. Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı kullandıysanız çağırmalısınız <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=nameWithType> burada uygulama.  
  
  **Büyük miktarlarda bellek tüketen veya nadir kaynakları tüketen nesneleri yönetilen.** Bu nesnelerin açıkça `Dispose` yöntemi serbest bunları, belirleyici olmayan şekilde çöp toplayıcı tarafından geri kazanılan, daha hızlı.  
  
Yöntem çağrısı bir sonlandırıcıdan gelirse (yani *disposing* olan `false`), yalnızca yönetilmeyen kaynakları serbest bırakan kod yürütülür. Çöp toplayıcı yok etme yönetilen nesneleri sonlandırma sırasında sırası tanımlı olmadığından bu çağırma `Dispose` aşırı değeriyle `false` Sonlandırıcı olabilecek yönetilen kaynakları serbest bırakmaya çalışmasını önler. zaten iadesi.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Dispose desenini bir temel sınıf için uygulama

Dispose desenini bir temel sınıf için uygularsanız, aşağıdakileri sağlamanız gerekir:  
  
> [!IMPORTANT]
> Bu düzen uygulayan tüm temel sınıflar için uygulamalıdır <xref:System.IDisposable.Dispose> ve `sealed` (`NotInheritable` Visual Basic'te).  
  
* A <xref:System.IDisposable.Dispose%2A> çağıran uygulama `Dispose(Boolean)` yöntemi.  
  
* A `Dispose(Boolean)` kaynakları serbest bırakma işini gerçekleştiren yöntemi.  
  
* Türetilen bir sınıf <xref:System.Runtime.InteropServices.SafeHandle> yönetilemeyen kaynağınızı (önerilir) veya bir geçersiz kılma sarmalar <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. <xref:System.Runtime.InteropServices.SafeHandle> Sınıf bir kod zorunda kalmanızı bir sonlandırıcı sağlar.  
  
Güvenli Tanıtıcı kullanan bir temel sınıf için dispose deseni uygulamada genel düzen aşağıda verilmiştir.  
  
[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
> Önceki örnekte bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> deseni göstermek için nesne; herhangi bir nesne öğesinden türetilen <xref:System.Runtime.InteropServices.SafeHandle> yerine kullanılabilir. Örnek değil düzgün örneği Not kendi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesne.  
  
Geçersiz kılan bir temel sınıf için dispose deseni uygulamada genel Düzen <xref:System.Object.Finalize%2A?displayProperty=nameWithType>.  
  
[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
> C# içinde geçersiz kılmanız <xref:System.Object.Finalize%2A?displayProperty=nameWithType> tanımlayarak bir [yok Edicisi](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Türetilen bir sınıf için dispose desenini uygulama

Uygulayan bir sınıftan türetilmiş bir sınıf <xref:System.IDisposable> arabirimini <xref:System.IDisposable>, temel sınıf çünkü uygulaması <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> kendi türetilmiş sınıflar tarafından devralınır. Onun yerine, türetilen bir sınıfa ilişkin olarak dispose desenini uygulamak için aşağıdakileri sağlarsınız:  
  
* A `protected Dispose(Boolean)` temel sınıf yöntemini geçersiz kılan ve türetilen sınıfın kaynaklarını serbest bırakma işini gerçekleştiren yöntemi. Bu yöntemini de çağırmalı `Dispose(Boolean)` yöntemi temel sınıf ve disposing durumu bağımsız değişkeni için geçirin.  
  
* Türetilen bir sınıf <xref:System.Runtime.InteropServices.SafeHandle> yönetilemeyen kaynağınızı (önerilir) veya bir geçersiz kılma sarmalar <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemi. <xref:System.Runtime.InteropServices.SafeHandle> Sınıf bir kod zorunda kalmanızı bir sonlandırıcı sağlar. Bir sonlandırıcı sağlarsanız, çağırmalıdır `Dispose(Boolean)` aşırı yüklemesine bir *disposing* bağımsız değişkeni `false`.  
  
Güvenli tanıtıcı kullanan bir türetilen sınıf için dispose deseni uygulamada genel düzen aşağıdaki gibidir:  
  
[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
> Önceki örnekte bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> deseni göstermek için nesne; herhangi bir nesne öğesinden türetilen <xref:System.Runtime.InteropServices.SafeHandle> yerine kullanılabilir. Örnek değil düzgün örneği Not kendi <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> nesne.  
  
Geçersiz kılan bir türetilen sınıf için dispose deseni uygulamada genel Düzen <xref:System.Object.Finalize%2A?displayProperty=nameWithType>:  
  
[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
> C# içinde geçersiz kılmanız <xref:System.Object.Finalize%2A?displayProperty=nameWithType> tanımlayarak bir [yok Edicisi](~/docs/csharp/programming-guide/classes-and-structs/destructors.md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Güvenli tanıtıcıları kullanma

Bir nesnenin sonlandırıcısı için kod yazmak, doğru yapılmaması durumunda sorunlara neden olabilecek karmaşık bir görevdir. Bu nedenle, oluşturmak öneririz <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> bir sonlandırıcı uygulamak yerine, nesneleri.  
  
Türetilen sınıflar <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfı atayarak ve serbest bırakma kesintisiz şekilde işleyicileri nesne kullanım ömrü sorunlarını basitleştirir. Uygulama etki alanı kaldırılırken çalıştırılması kesin olan kritik bir sonlandırıcı içerirler. Güvenli Tanıtıcı kullanmanın avantajları hakkında daha fazla bilgi için bkz: <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>. Aşağıdaki türetilmiş sınıflar içinde <xref:Microsoft.Win32.SafeHandles> ad alanı güvenli tanıtıcılar sağlar:  
  
* <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>, Ve <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> dosyalar, bellek eşlemeli dosyalar ve kanallar için bir sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> Bellek görünümleri için bir sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>, Ve <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> şifreleme yapıları için bir sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> Kayıt defteri anahtarları için bir sınıf.  
  
* <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> Bekleme tanıtıcıları için bir sınıf.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Bir temel sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnekte, bir temel sınıf için dispose deseni gösterilmektedir `DisposableStreamResource`yönetilmeyen kaynakları kapsüllemek üzere güvenli bir tanıtıcı kullanan,. Tanımladığı bir `DisposableResource` kullanan sınıf bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> sarmak için bir <xref:System.IO.Stream> açık bir dosyayı temsil eden nesne. `DisposableResource` Yöntemi de içeren tek bir özelliğe `Size`, dosya akışındaki toplam bayt sayısını döndürür.  
  
[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Bir türetilen sınıfa ilişkin olarak dispose deseni uygulamak için güvenli tanıtıcı kullanma

Aşağıdaki örnekte, bir türetilen sınıf için dispose deseni gösterilmektedir `DisposableStreamResource2`, öğesinden devralan `DisposableStreamResource` önceki örnekte gösterilen sınıfı. Sınıf ek bir yöntem ekler `WriteFileInfo`ve kullandığı bir <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> ve yazılabilir dosyanın tanıtıcısı sarmak için.  
  
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
