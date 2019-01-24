---
title: 'Nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, reflection-only loader context
- assemblies [.NET Framework], loading for reflection
- attributes [.NET Framework], retrieving
- assemblies [.NET Framework], reflection-only loader context
- reflection-only loader context
ms.assetid: 9818b660-52f5-423d-a9af-e75163aa7068
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eeef33745ebc8209fc7f69a9337af4093c1e8a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567054"
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Nasıl yapılır: Salt yansıma bağlamına derlemeleri yükleme
Yalnızca yansıma yükleme bağlamı, diğer platformlar için veya .NET Framework'ün diğer sürümleri için derlenmiş derlemeleri incelemenize olanak tanır. Bu bağlamı yüklenen kodunu yalnızca incelenebilir; yürütülemez. Oluşturucular yürütülemiyor çünkü bu nesneler oluşturulamayacağını, anlamına gelir. Kod olarak yürütülemiyor çünkü bağımlılıkları otomatik olarak yüklenmez. Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemelisiniz.  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Yük salt yansıma bağlamına bir derlemeyi yüklemek için  
  
1.  Kullanım <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> görünen adı, verilen derlemeyi yüklemek için yöntem aşırı yüklemesini veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yolu verilen derlemeyi yüklemek için yöntemi. Derleme ikili bir görüntüsüdür kullanırsanız <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> yöntemi aşırı yüklemesi.  
  
    > [!NOTE]
    >  Yalnızca yansıma bağlam, .NET Framework sürümü yürütme bağlamı dışında bir sürümünden bir mscorlib.dll sürümü yüklemek için kullanamazsınız.  
  
2.  Derleme bağımlılıkları varsa <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> yöntemi yüklenmemesi bunları. Bunları incelemeniz gerekiyorsa, bunları kendiniz yüklemelisiniz.  
  
3.  Derlemenin kullanarak bir derleme salt yansıma bağlamına yüklü olup olmadığını <xref:System.Reflection.Assembly.ReflectionOnly%2A> özelliği.  
  
4.  Öznitelikleri derlemenin veya derlemedeki türleri uygulandıysa, bu öznitelikleri kullanarak incelemek <xref:System.Reflection.CustomAttributeData> salt yansıma bağlamında kod yürütmesine girişimde bulunulmaz emin olmak için sınıf. Uygun aşırı yüklemesini kullanın <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> elde etmek için yöntemi <xref:System.Reflection.CustomAttributeData> bir derleme, üye, modül veya parametre uygulanan öznitelikleri temsil eden nesneleri.  
  
    > [!NOTE]
    >  Derleme veya içeriğine uygulanan öznitelikleri derlemede tanımlanan veya başka bir derlemede salt yansıma bağlamına yüklenen tanımlanabilir. Öznitelikleri tanımlandığı önceden bildirmek için hiçbir yolu yoktur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, salt yansıma bağlamına yüklenen bir derlemeye uygulanan öznitelikleri incelemek gösterilmektedir.  
  
 Kod örneği, iki oluşturucu ve bir özellik ile özel bir öznitelik tanımlar. Öznitelik, derleme, derleme içinde bildirilen bir türe, türü bir yönteme ve yönteminin bir parametresi için uygulanır. Yürütüldüğünde, derlemenin kendisi salt yansıma bağlamına yükler ve ona ve türler ve üyeler içerdiği için uygulanan özel öznitelikler hakkında bilgi görüntüler.  
  
> [!NOTE]
>  Kod örneği basitleştirmek için derleme yükler ve kendisini inceler. Normalde, yürütme bağlamı ve salt yansıma bağlamı yüklenen aynı derlemenin bulmak beklediğiniz değil.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>
- <xref:System.Reflection.Assembly.ReflectionOnly%2A>
- <xref:System.Reflection.CustomAttributeData>
