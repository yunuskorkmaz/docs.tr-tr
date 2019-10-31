---
title: Yönetilmeyen Kaynakları Temizleme
ms.date: 03/30/2017
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
ms.openlocfilehash: 04bed819b472abe23ae6a9e89de149e715272505
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141358"
---
# <a name="cleaning-up-unmanaged-resources"></a>Yönetilmeyen Kaynakları Temizleme

Uygulamanızın oluşturduğu nesnelerin çoğu için, ' i kullanabilirsiniz. Bellek yönetimini işlemek için NET 'in çöp toplayıcısı. Ancak, yönetilmeyen kaynaklar içeren nesneler oluşturduğunuzda, uygulamanızda kullanmayı bitirdiğinizde, bu kaynakları açıkça serbest bırakmanız gerekir. En sık karşılaşılan yönetilmeyen kaynak türleri, dosyalar, pencereler, ağ bağlantıları veya veritabanı bağlantıları gibi işletim sistemi kaynaklarını saran nesnelerdir. Çöp toplayıcı yönetilmeyen bir kaynağı kapsülleyen bir nesnenin kullanım ömrünü izleyebilir olsa da, yönetilmeyen kaynağı nasıl serbest bırakacağını ve temizleyeceğini bilmez.

Türleriniz yönetilmeyen kaynaklar ise, aşağıdakileri yapmanız gerekir:

- [Dispose modelini](../../../docs/standard/design-guidelines/dispose-pattern.md)uygulayın. Bu, yönetilmeyen kaynakların belirleyici sürümünü etkinleştirmek için bir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulama sağlamanızı gerektirir. Nesne (ve kullandığı kaynaklar) artık gerekli olmadığında, bir tür tüketicisini <xref:System.IDisposable.Dispose%2A> çağırır. <xref:System.IDisposable.Dispose%2A> yöntemi, yönetilmeyen kaynakları hemen serbest bırakır.

- Bir tür tüketicisinin <xref:System.IDisposable.Dispose%2A>çağırmayı unutması durumunda, yönetilmeyen kaynaklarınızın serbest bırakılacağını sağlayın. Bunu yapmak için iki yol vardır:

  - Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı kullanın. Önerilen yöntem budur. Güvenli tutamaçlar <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıfından türetilir ve güçlü bir <xref:System.Object.Finalize%2A> yöntemi içerir. Güvenli bir tanıtıcı kullandığınızda, <xref:System.IDisposable> arabirimini uygulamanız ve <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamanızda güvenli tanıtıcıınızın <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> yöntemini çağırmanız yeterlidir. <xref:System.IDisposable.Dispose%2A> yöntemi çağrılmadıysanız, güvenli tanıtıcının sonlandırıcısı çöp toplayıcı tarafından otomatik olarak çağrılır.

    —veya—

  - <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yöntemini geçersiz kılın. Sonlandırma, bir türün tüketicisini belirleyici olarak atmak için <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> çağıramazsa yönetilmeyen kaynakların belirleyici olmayan bir şekilde serbest olmasına olanak sağlar. Ancak, nesne sonlandırma karmaşık ve hataya açık bir işlem olduğundan, kendi sonlandırıcınızı sağlamak yerine güvenli tanıtıcı kullanmanız önerilir.

Daha sonra, bu türden tüketiciler, yönetilmeyen kaynaklar tarafından kullanılan belleği açmak için doğrudan <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamanızı çağırabilir. Bir <xref:System.IDisposable.Dispose%2A> yöntemi düzgün bir şekilde uyguladığınızda, güvenli işleyicinizdeki <xref:System.Object.Finalize%2A> yöntemi veya <xref:System.Object.Finalize%2A?displayProperty=nameWithType> yönteminin kendi geçersiz kılması <xref:System.IDisposable.Dispose%2A> yönteminin çağrılmaması durumunda kaynakları temizlemek için bir güvenlik önlemi haline gelir.

## <a name="in-this-section"></a>Bu Bölümde

[Dispose yöntemi uygulama](../../../docs/standard/garbage-collection/implementing-dispose.md) Yönetilmeyen kaynakları serbest bırakmak için [Dispose deseninin](../../../docs/standard/design-guidelines/dispose-pattern.md) nasıl uygulanacağını açıklar.

[IDisposable uygulayan nesneleri kullanma](../../../docs/standard/garbage-collection/using-objects.md) Bir türün tüketicilerinin <xref:System.IDisposable.Dispose%2A> uygulamasının çağrıldığından nasıl emin olduğunu açıklar. Bunu yapmak için C# `using` deyimin veya Visual Basic `Using` ifadesinin kullanılmasını öneririz.

## <a name="reference"></a>Başvuru

<xref:System.IDisposable?displayProperty=nameWithType>\
Yönetilmeyen kaynakları serbest bırakmak için <xref:System.IDisposable.Dispose%2A> yöntemini tanımlar.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Yönetilmeyen kaynaklar <xref:System.IDisposable.Dispose%2A> yöntemi tarafından yayımlanamadığında nesne sonlandırması sağlar.

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Sonlandırmayı bastırır. Bu yöntem, sonlandırıcının yürütülmesini engellemek için bir `Dispose` yönteminden geleneksel çağırılır.
