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
ms.openlocfilehash: f21126361ce69ab14d18e12d2787b2c264116b02
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921533"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme
Bir uygulama etki alanına bir derlemeyi yüklemek için birkaç yol vardır. Önerilen yol `static` ,`Shared` sınıfının<xref:System.Reflection.Assembly?displayProperty=nameWithType> (Visual Basic) <xref:System.Reflection.Assembly.Load%2A> sınıfında kullanılır. Derlemelerin yüklenebilme diğer yolları şunlardır:  
  
- Sınıfının<xref:System.Reflection.Assembly> yöntemi, <xref:System.Reflection.Assembly.LoadFrom%2A> dosya konumu verilen bir derlemeyi yükler. Derlemeleri bu yöntemle yüklemek farklı bir yük bağlamı kullanır.  
  
- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Ve<xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri bir derlemeyi yalnızca yansıma bağlamına yükler. Bu içeriğe yüklenen derlemeler incelenebilir ancak yürütülmeyebilir, diğer platformları hedefleyen derlemelerin incelenmesi sağlanır. Bkz [. nasıl yapılır: Derlemeleri yalnızca yansıma bağlamına](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)yükleyin.  
  
> [!NOTE]
> Yalnızca yansıma bağlamı .NET Framework sürüm 2,0 ' de yenidir.  
  
- <xref:System.AppDomain.CreateInstance%2A> Sınıfının ve <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> gibi yöntemleri bir uygulama etki alanına derlemeler yükleyebilir. <xref:System.AppDomain>  
  
- <xref:System.Type> Sınıfının <xref:System.Type.GetType%2A> yöntemi derlemeleri yükleyebilir.  
  
- <xref:System.AppDomain?displayProperty=nameWithType> Sınıfının yöntemi derlemeleri yükleyebilir, ancak birincil olarak com birlikte çalışabilirlik için kullanılır. <xref:System.AppDomain.Load%2A> Derlemeleri, çağrıldığı uygulama etki alanından başka bir uygulama etki alanına yüklemek için kullanılmamalıdır.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez. Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.  
  
 Yüklenen derlemelerdeki tam zamanında (JıT) derlenmiş kodun uygulama etki alanları arasında paylaşılma şeklini belirtebilirsiniz. Daha fazla bilgi için bkz. [uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, geçerli uygulama etki alanına "example. exe" veya "example. dll" adlı bir derlemeyi yükler, derlemeden adlı `Example` bir tür alır, bu tür için adlı `MethodA` parametresiz bir yöntemi alır ve yöntemini yürütür. Yüklü bir derlemeden bilgi alma hakkında ayrıntılı bir tartışma için bkz. [dinamik olarak yükleme ve türleri kullanma](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)
- [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)
- [Nasıl yapılır: Derlemeleri yalnızca yansıma Içeriğine yükle](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [Uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies)
