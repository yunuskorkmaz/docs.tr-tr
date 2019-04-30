---
title: 'Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51c1ac87cf9111504ba99efa25f6fca2bb0b63df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705655"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme
Uygulama etki alanına bir derlemeyi yüklemek için birkaç yolu vardır. Kullanmak için önerilen yoldur `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.Load%2A> yöntemi <xref:System.Reflection.Assembly?displayProperty=nameWithType> sınıfı. Derlemeleri yüklenebilir diğer yolları:  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A> Yöntemi <xref:System.Reflection.Assembly> sınıfı, dosya konumu verilen bir derleme yükler. Bu yöntemle derlemeler yüklemek, farklı yükleme bağlamı kullanır.  
  
- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri salt yansıma bağlamına bir derlemeyi yüklemek. Bu bağlamı yüklenen derlemeler incelenir, ancak yürütülmedi, diğer platformları hedefleyen derlemeleri incelenmesi izin verme. Bkz: [nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  Yalnızca yansıma bağlamı, .NET Framework 2.0 sürümünde yenidir.  
  
- Yöntemler gibi <xref:System.AppDomain.CreateInstance%2A> ve <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> , <xref:System.AppDomain> sınıfı, bir uygulama etki alanına derlemeler yükleyebilir.  
  
- <xref:System.Type.GetType%2A> Yöntemi <xref:System.Type> sınıfı derlemeleri yükleyebilir.  
  
- <xref:System.AppDomain.Load%2A> Yöntemi <xref:System.AppDomain?displayProperty=nameWithType> sınıfı derlemeleri yükleyebilirsiniz ancak öncelikle COM birlikte çalışabilirlik için kullanılır. İçinden çağrıldığı uygulama etki alanından başka bir uygulama etki alanına derlemeler yüklemek için kullanılmamalıdır.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklü çalışma zamanı daha yüksek bir sürüm numarasına sahip .NET Framework sürümü ile derlenen bütünleştirilmiş yüklemez. Bu sürüm numarasının büyük ve küçük bileşenleri birleşimi için geçerlidir.  
  
 Uygulama etki alanları arasında paylaşılan just-in-time (JIT) derlenmiş kodunun yüklenen derlemelerin yolu belirtebilirsiniz. Daha fazla bilgi için [uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod yüklerini geçerli uygulama etki alanına "example.exe" veya "example.dll" adlı bir derleme adlı bir tür alır `Example` adlı bir parametresiz yöntemin, derlemenin alır `MethodA` , yazın ve yöntemini yürütür. Kapsamlı bir açıklama yüklenen derlemeden bilgi edinme hakkında bilgi için bkz: [dinamik olarak yükleme ve türleri kullanarak](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
- [Nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [Uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies)
