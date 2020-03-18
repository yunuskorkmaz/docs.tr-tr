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
ms.openlocfilehash: e05cfb949ee3f206f212ca7015f3ff4c22cd2a12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423032"
---
# <a name="cleaning-up-unmanaged-resources"></a>Yönetilmeyen Kaynakları Temizleme

Uygulamanızın oluşturduğu nesnelerin çoğu için güvenebilirsiniz. NET'in çöp toplayıcısı bellek yönetimini halledecek. Ancak, yönetilmeyen kaynaklar içeren nesneler oluşturduğunuzda, uygulamanızda kullanmayı bitirdiğinizde, bu kaynakları açıkça serbest bırakmanız gerekir. En sık karşılaşılan yönetilmeyen kaynak türleri, dosyalar, pencereler, ağ bağlantıları veya veritabanı bağlantıları gibi işletim sistemi kaynaklarını saran nesnelerdir. Çöp toplayıcı yönetilmeyen bir kaynağı kapsülleyen bir nesnenin kullanım ömrünü izleyebilir olsa da, yönetilmeyen kaynağı nasıl serbest bırakacağını ve temizleyeceğini bilmez.

Türleriniz yönetilmeyen kaynaklar ise, aşağıdakileri yapmanız gerekir:

- Bertaraf [deseni](implementing-dispose.md)uygulayın. Bu, yönetilmeyen <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> kaynakların deterministik serbest bırakılmasını etkinleştirmek için bir uygulama sağlamanızı gerektirir. Nesne (ve kullandığı <xref:System.IDisposable.Dispose%2A> kaynaklar) artık ihtiyaç duyulmadığında, türün bir tüketicisi çağırır. Yöntem, <xref:System.IDisposable.Dispose%2A> yönetilmeyen kaynakları hemen serbest bırakır.

- Türünüzdeki bir tüketicinin aramayı <xref:System.IDisposable.Dispose%2A>unutması durumunda, yönetilmeyen kaynaklarınızın serbest bırakılmasını sağlayın. Bunu yapmak için iki yol vardır:

  - Yönetilmeyen kaynağınızı sarmak için güvenli bir tanıtıcı kullanın. Önerilen yöntem budur. Güvenli tutamaçları <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> sınıftan türetilmiştir <xref:System.Object.Finalize%2A> ve sağlam bir yöntem içerir. Güvenli bir tutamaç kullandığınızda, <xref:System.IDisposable> arabirimi uygulamanız yeterlidir <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> ve uygulamanızda güvenli iş talının yöntemini ararsınız. <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> Emniyet kolunun sonlandırıcısı, <xref:System.IDisposable.Dispose%2A> yöntemi çağrılmazsa çöp toplayıcıtarafından otomatik olarak çağrılır.

    —veya—

  - <xref:System.Object.Finalize%2A?displayProperty=nameWithType> Yöntemi geçersiz kılın. Sonlandırma, bir tür tüketici nin bunları deterministically elden çıkarmak için <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> aramak için başarısız olduğunda yönetilmeyen kaynakların nonterministic serbest sağlar. Ancak, nesne sonlandırma karmaşık ve hataya açık bir işlem olduğundan, kendi sonlandırıcınızı sağlamak yerine güvenli tanıtıcı kullanmanız önerilir.

Daha sonra türünün tüketicileri, uygulamanızı <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> doğrudan yönetilmeyen kaynaklar tarafından kullanılan boş belleğe çağırabilir. Bir yöntemi düzgün <xref:System.IDisposable.Dispose%2A> bir şekilde uyguladığınızda, <xref:System.Object.Finalize%2A> güvenli iştünüzün yöntemi <xref:System.Object.Finalize%2A?displayProperty=nameWithType> veya yöntemin kendi geçersiz kılma yöntemi, <xref:System.IDisposable.Dispose%2A> yöntemin çağrılması durumunda kaynakları temizlemek için bir koruma haline gelir.

## <a name="in-this-section"></a>Bu Bölümde

[Elden Çıkarma Yönteminin Uygulanması](../../../docs/standard/garbage-collection/implementing-dispose.md) Yönetilmeyen kaynakları serbest bırakmak için [elden çıkarma deseni](implementing-dispose.md) nasıl uygulanacağını açıklar.

[IDisposable Uygulayan Nesneleri Kullanma](../../../docs/standard/garbage-collection/using-objects.md) Bir türdeki tüketicilerin, uygulamanın çağrılmasını nasıl sağladıklarını <xref:System.IDisposable.Dispose%2A> açıklar. Bunu yapmak için `using` C# deyimini `Using` veya Visual Basic deyimini kullanmanızı öneririz.

## <a name="reference"></a>Başvuru

<xref:System.IDisposable?displayProperty=nameWithType>\
Yönetilmeyen <xref:System.IDisposable.Dispose%2A> kaynakları serbest bırakma yöntemini tanımlar.

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
Yöntem tarafından yönetilmeyen kaynaklar serbest bırakılmazsa nesne sonlandırma sağlar. <xref:System.IDisposable.Dispose%2A>

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
Sonlandırmayı bastırır. Bu yöntem, bir sonlandırıcının yürütülmesini önlemek için alışılmış bir `Dispose` yöntemden çağrılır.
