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
ms.openlocfilehash: 0925f7445c4451f61bd1c878cc66300d62bdc855
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-load-assemblies-into-an-application-domain"></a>Nasıl yapılır: Uygulama Etki Alanına Derlemeler Yükleme
Uygulama etki alanına bir derlemeyi yüklemek için birkaç yol vardır. Kullanmak için önerilen yoldur `static` (`Shared` Visual Basic'te) <xref:System.Reflection.Assembly.Load%2A> yöntemi <xref:System.Reflection.Assembly?displayProperty=nameWithType> sınıfı. Derlemeleri yüklenebilir diğer yolları şunlardır:  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A> Yöntemi <xref:System.Reflection.Assembly> sınıfı dosya konumunu verilen bir derleme yükler. Bu yöntemle derlemeleri yükleme farklı bir yük bağlamını kullanır.  
  
-   <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> Ve <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yöntemleri salt yansıma bağlamına bir derlemeyi yüklemek. Bu bağlamına yüklenmiş derlemeleri incelenmesi, ancak yürütülmedi, diğer platformlar hedef derlemeleri incelenmesi izin verme. Bkz: [nasıl yapılır: salt yansıma bağlamına derlemeleri yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
> [!NOTE]
>  Yalnızca yansıma bağlamı, .NET Framework 2.0 sürümünde yenidir.  
  
-   Gibi yöntemler <xref:System.AppDomain.CreateInstance%2A> ve <xref:System.AppDomain.CreateInstanceAndUnwrap%2A> , <xref:System.AppDomain> sınıfı, bir uygulama etki alanına derlemeler yükleyebilirsiniz.  
  
-   <xref:System.Type.GetType%2A> Yöntemi <xref:System.Type> sınıfı derlemeleri yükleyebilirsiniz.  
  
-   <xref:System.AppDomain.Load%2A> Yöntemi <xref:System.AppDomain?displayProperty=nameWithType> sınıfı derlemelerini yüklemek için COM birlikte çalışabilirliği öncelikle kullanılır ancak. İçinden adlandırılır uygulama etki alanı dışındaki bir uygulama etki alanına derlemeler yüklemek için kullanılmamalıdır.  
  
> [!NOTE]
>  .NET Framework sürüm 2.0 ile başlayarak, çalışma zamanı şu anda yüklenen çalışma zamanı'den daha yüksek bir sürüm numarası .NET Framework sürümü için derlenmiş bir derlemeyi yüklemez. Bu sürüm numarası birincil ve ikincil bileşenlerinin birleşimi için geçerlidir.  
  
 Uygulama etki alanları arasında tam zamanında (JIT) derlenmiş kod yüklenen derlemelerden şekilde paylaşılan belirtebilirsiniz. Daha fazla bilgi için bkz: [uygulama etki alanları ve derlemeler](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod yükleri geçerli uygulama etki alanına "example.exe" veya "example.dll" adlı bir derleme alır adlı tür `Example` derlemesinden adlı parametresiz bir yöntemi alır `MethodA` , yazın ve yöntemini yürütür. Kapsamlı bir açıklama yüklenen bir derlemeden bilgi edinme hakkında bilgi için bkz: [dinamik olarak yükleme ve türleri kullanma](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md).  
  
 [!code-cpp[System.AppDomain.Load#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source2.cpp#2)]
 [!code-csharp[System.AppDomain.Load#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source2.cs#2)]
 [!code-vb[System.AppDomain.Load#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 [Uygulama etki alanları ile programlama](application-domains.md#programming-with-application-domains)  
 [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [Uygulama Etki Alanlarını Kullanma](../../../docs/framework/app-domains/use.md)  
 [Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)  
 [Uygulama Etki Alanları ve Derlemeler](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
