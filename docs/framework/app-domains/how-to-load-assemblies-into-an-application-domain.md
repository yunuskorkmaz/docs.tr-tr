---
title: 'Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme'
description: .NET 'teki bir uygulama etki alanına derlemeler yüklemeyi öğrenin. Önerilen yol, System. Reflection. Assembly içinde statik (veya paylaşılan) yükleme yöntemini kullanmaktır.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, loading assemblies
- loading assemblies
ms.assetid: 1432aa2d-bd83-4346-bf3b-a1b7920e2aa9
ms.openlocfilehash: c91c70625b79002e9297755dfdfac8aa6e283208
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104751"
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme
Bir uygulama etki alanına bir derlemeyi yüklemek için birkaç yol vardır. Önerilen yol, `static` `Shared` sınıfının (Visual Basic) <xref:System.Reflection.Assembly.Load%2A> sınıfında kullanılır <xref:System.Reflection.Assembly?displayProperty=nameWithType> . Derlemelerin yüklenebilme diğer yolları şunlardır:  
  
- <xref:System.Reflection.Assembly.LoadFrom%2A>Sınıfının yöntemi, <xref:System.Reflection.Assembly> dosya konumu verilen bir derlemeyi yükler. Derlemeleri bu yöntemle yüklemek farklı bir yük bağlamı kullanır.  
  
- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>Ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri bir derlemeyi yalnızca yansıma bağlamına yükler. Bu içeriğe yüklenen derlemeler incelenebilir ancak yürütülmeyebilir, diğer platformları hedefleyen derlemelerin incelenmesi sağlanır. Bkz. [nasıl yapılır: derlemeleri yalnızca yansıma bağlamına yükleme](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
> Yalnızca yansıma bağlamı .NET Framework sürüm 2,0 ' de yenidir.  
  
- <xref:System.AppDomain.CreateInstance%2A>Sınıfının ve gibi yöntemleri <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> <xref:System.AppDomain> bir uygulama etki alanına derlemeler yükleyebilir.  
  
- <xref:System.Type.GetType%2A> <xref:System.Type> Sınıfının yöntemi derlemeleri yükleyebilir.  
  
- <xref:System.AppDomain.Load%2A> <xref:System.AppDomain?displayProperty=nameWithType> Sınıfının yöntemi derlemeleri yükleyebilir, ancak BIRINCIL olarak com birlikte çalışabilirlik için kullanılır. Derlemeleri, çağrıldığı uygulama etki alanından başka bir uygulama etki alanına yüklemek için kullanılmamalıdır.  
  
> [!NOTE]
> .NET Framework sürüm 2,0 ' den başlayarak, çalışma zamanı, yüklü olan çalışma zamanından daha yüksek bir sürüm numarasına sahip .NET Framework bir sürümle derlenen bir derlemeyi yüklemez. Bu, sürüm numarasının büyük ve küçük bileşenlerinin birleşimi için geçerlidir.  
  
 Yüklenen derlemelerdeki tam zamanında (JıT) derlenmiş kodun uygulama etki alanları arasında paylaşılma şeklini belirtebilirsiniz. Daha fazla bilgi için bkz. [uygulama etki alanları ve derlemeler](application-domains.md#application-domains-and-assemblies).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, geçerli uygulama etki alanına "example.exe" veya "example.dll" adlı bir derlemeyi yükler, derlemeden adlı bir tür alır, `Example` Bu tür için adlı parametresiz bir yöntemi alır `MethodA` ve yöntemini yürütür. Yüklü bir derlemeden bilgi alma hakkında ayrıntılı bir tartışma için bkz. [dinamik olarak yükleme ve türleri kullanma](../reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- [Uygulama etki alanlarıyla programlama](application-domains.md#programming-with-application-domains)
- [Yansıma](../reflection-and-codedom/reflection.md)
- [Uygulama Etki Alanlarını Kullanma](use.md)
- [Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)
- [Uygulama Etki Alanları ve derlemeler](application-domains.md#application-domains-and-assemblies)
