---
title: 'Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ab0224dd0452003f1d43a314d03aaca0fe04fda
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-load-assemblies-into-the-reflection-only-context"></a>Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme
Yalnızca yansıma yükleme bağlamı, diğer platformlar için veya diğer .NET Framework sürümleri için derlenmiş derlemeleri incelemek sağlar. Bu bağlamına yüklenen kod yalnızca incelenebilir; yürütülemez. Oluşturucular yürütülemiyor çünkü bu nesneleri oluşturulamayacağını, anlamına gelir. Kod yürütülemiyor çünkü bağımlılıkları otomatik olarak yüklenmez. Bunları inceleyin ihtiyacınız varsa, bunları kendiniz yüklemelisiniz.  
  
### <a name="to-load-an-assembly-into-the-reflection-only-load-context"></a>Yalnızca yansıma yük bağlamına bir derlemeyi yüklemek için  
  
1.  Kullanım <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.String%29> görünen adını, belirtilen derlemeyi yüklemeye yöntemi aşırı yüklemesini veya <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A> yolunu verilen derlemeyi yüklemek için yöntem. Derleme ikili görüntü ise kullanın <xref:System.Reflection.Assembly.ReflectionOnlyLoad%28System.Byte%5B%5D%29> yöntemi aşırı yüklemesini.  
  
    > [!NOTE]
    >  Yalnızca yansıma bağlamı dışında yürütme bağlamı sürümünde .NET Framework sürümünün mscorlib.dll bir sürümünü yüklemek için kullanamazsınız.  
  
2.  Derleme bağımlılıkları varsa <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A> yöntemi yüklenmemesi bunları. Bunları inceleyin ihtiyacınız varsa, bunları kendiniz yüklemelisiniz.  
  
3.  Derlemenin kullanarak, bir derlemeyi salt yansıma bağlamına yüklü olup olmadığını belirlemek <xref:System.Reflection.Assembly.ReflectionOnly%2A> özelliği.  
  
4.  Öznitelikleri derlemenin veya derlemedeki türleri uygulandıysa, bu öznitelikleri kullanarak inceleyin <xref:System.Reflection.CustomAttributeData> sınıfı salt yansıma bağlamında kod yürütmek için girişimde bulunulmaz emin olun. Uygun kullanın <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> elde etmek için yöntemi <xref:System.Reflection.CustomAttributeData> bir derleme, üye, modül veya parametre uygulanan öznitelikleri temsil eden nesne.  
  
    > [!NOTE]
    >  Derleme veya içeriğinin uygulanan öznitelikleri derlemede tanımlanan veya başka bir derlemede salt yansıma bağlamına yüklenen tanımlanabilir. Önceden öznitelikleri tanımlandığı bildirmek için bir yolu yoktur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde salt yansıma bağlamına yüklenen bir derleme uygulanan öznitelikleri inceleyin gösterilmektedir.  
  
 Kod örneği iki oluşturucular ve bir özellik ile özel bir öznitelik tanımlar. Öznitelik, derleme, derlemede bildirilen bir türe, türü yöntemi için ve yönteminin bir parametresi için uygulanır. Çalıştırıldığında, derleme kendisini salt yansıma bağlamına yükler ve onu ve türleri ve içerdiği üyelerine uygulanan özel öznitelikler hakkında bilgi görüntüler.  
  
> [!NOTE]
>  Kod örneği basitleştirmek için derleme yükler ve kendisini inceler. Normalde, yürütme bağlamı ve yalnızca yansıma bağlam yüklenen aynı bütünleştirilmiş bulmak beklediğiniz değil.  
  
 [!code-cpp[CustomAttributeData#1](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source.cpp#1)]
 [!code-csharp[CustomAttributeData#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source.cs#1)]
 [!code-vb[CustomAttributeData#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A>  
 <xref:System.Reflection.Assembly.ReflectionOnly%2A>  
 <xref:System.Reflection.CustomAttributeData>
