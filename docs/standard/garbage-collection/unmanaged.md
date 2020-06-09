---
title: Yönetilmeyen kaynakları Temizleme
description: Dosyalar, Windows, & ağı veya veritabanı bağlantıları gibi .NET atık toplayıcısı tarafından işlenmeyen yönetilmeyen kaynakları temizleme bölümüne bakın.
ms.date: 05/13/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: 07a8d754f1fc2612ae53407fa1b12a1eab7e38f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599844"
---
# <a name="cleaning-up-unmanaged-resources"></a>Yönetilmeyen kaynakları Temizleme

Uygulamanızın oluşturduğu nesnelerin çoğu için, bellek yönetimini işlemek üzere [.NET çöp toplayıcısına](index.md) güvenebilirsiniz. Ancak, yönetilmeyen kaynakları içeren nesneler oluşturduğunuzda, bunları kullanmayı bitirdiğinizde bu kaynakları açıkça serbest bırakmanız gerekir. Yönetilmeyen kaynakların en yaygın türleri, dosyalar, Windows, ağ bağlantıları veya veritabanı bağlantıları gibi işletim sistemi kaynaklarını çevreeden nesnelerdir. Çöp toplayıcı yönetilmeyen bir kaynağı kapsülleyen bir nesnenin kullanım ömrünü izleyebilir olsa da, yönetilmeyen kaynağı nasıl serbest bırakacağını ve temizleyeceğini bilmez.

Türleriniz yönetilmeyen kaynaklar ise, aşağıdakileri yapmanız gerekir:

- [Dispose modelini](implementing-dispose.md)uygulayın. Bu <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> , yönetilmeyen kaynakların belirleyici sürümünü etkinleştirmek için bir uygulama sağlamanızı gerektirir. <xref:System.IDisposable.Dispose%2A>Nesne (ve kullandığı kaynaklar) artık gerekli olmadığında, bir tür tüketicisini çağırır. <xref:System.IDisposable.Dispose%2A>Yöntemi, yönetilmeyen kaynakları hemen serbest bırakır.

- Bir tür tüketicisinin çağırmak için unutması durumunda <xref:System.IDisposable.Dispose%2A> , yönetilmeyen kaynaklarınızın serbest bırakılması için bir yol sağlayın. Bunu yapmak için iki yol vardır:

  - Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı kullanın. Önerilen yöntem budur. Güvenli işleyiciler <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> soyut sınıftan türetilir ve güçlü bir <xref:System.Object.Finalize%2A> yöntem içerir. Güvenli bir tanıtıcı kullandığınızda, yalnızca <xref:System.IDisposable> arabirimini uygular ve uygulamanızda güvenli işleyiciniz <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> yöntemini çağırın <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> . Güvenli tanıtıcının sonlandırıcısı, yöntemi çağrılmadıysanız çöp toplayıcı tarafından otomatik olarak çağrılır <xref:System.IDisposable.Dispose%2A> .

    —**veya**—

  - Yöntemini geçersiz kılın <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . Sonlandırma, bir türün tüketicisi belirleyici olarak atıldığında yönetilmeyen kaynakların belirleyici olmayan serbest olmasına olanak sağlar <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> . Yöntemi geçersiz kılarak bir [Sonlandırıcı](../../csharp/programming-guide/classes-and-structs/destructors.md) tanımlayın <xref:System.Object.Finalize%2A?displayProperty=nameWithType> .

  > [!WARNING]
  > Ancak, nesne sonlandırma karmaşık ve hataya açık bir işlem olabileceğinden, kendi sonlandırıcısını sağlamak yerine güvenli bir tanıtıcı kullanmanızı öneririz.

Daha sonra, bu tür tüketicileri, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> yönetilmeyen kaynaklar tarafından kullanılan belleği açmak için doğrudan uygulamanızı çağırabilir. Bir yöntemi düzgün bir şekilde uyguladığınızda <xref:System.IDisposable.Dispose%2A> , güvenli tanıtıcının <xref:System.Object.Finalize%2A> yöntemi veya kendi yöntemin geçersiz kılınması, <xref:System.Object.Finalize%2A?displayProperty=nameWithType> <xref:System.IDisposable.Dispose%2A> yöntemin çağrılmaması durumunda kaynakları temizlemek için bir güvenlik önlemi haline gelir.

## <a name="in-this-section"></a>Bu bölümde

[Dispose yöntemi uygulamak](implementing-dispose.md) , yönetilmeyen kaynakları serbest bırakmak için Dispose deseninin nasıl uygulanacağını açıklar.

[Uygulayan `IDisposable` nesneleri kullanma](using-objects.md) bir türün tüketicilerinin uygulamanın çağrılması için nasıl emin olduğunu açıklar <xref:System.IDisposable.Dispose%2A> . `using`Bunu yapmak Için C# (veya Visual Basic `Using` ) ifadesinin kullanılmasını öneririz.

## <a name="reference"></a>Başvuru

| Tür/üye | Açıklama |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | <xref:System.IDisposable.Dispose%2A>Yönetilmeyen kaynakları serbest bırakma yöntemini tanımlar. |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | Yönetilmeyen kaynaklar yöntemi tarafından yayımlanamadığında nesne sonlandırması sağlar <xref:System.IDisposable.Dispose%2A> . |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | Sonlandırmayı bastırır. Bu yöntem, `Dispose` sonlandırıcının yürütülmesini engellemek için bir yöntemden geleneksel çağırılır. |
