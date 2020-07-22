---
title: 'Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama'
description: Bkz. .NET 'te yansıma kullanarak bir temsilciyi bağlama. Mevcut bir yöntemi yansıma aracılığıyla gerekli türleri alarak olaya bağlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], adding event handlers with reflection
- reflection, adding event-handler delegates
- delegates [.NET Framework], adding event handlers with reflection
ms.assetid: 076ee62d-a964-449e-a447-c31b33518b81
ms.openlocfilehash: b5d93efd278a53a4e6382f2321918e58ead55899
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865092"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama
Derlemeleri yüklemek ve çalıştırmak için yansıma kullandığınızda, `+=` olayları bağlamak için C# işleci veya Visual Basic [AddHandler ifadesiyle](../../visual-basic/language-reference/statements/addhandler-statement.md) benzer dil özelliklerini kullanamazsınız. Aşağıdaki yordamlarda, tüm gerekli türleri yansıma aracılığıyla alarak bir olaya mevcut bir yöntemi nasıl yedekleyerek, yansıma yayma kullanarak dinamik bir yöntem oluşturma ve bir olaya bağlama işlemleri gösterilmektedir.  
  
> [!NOTE]
> Bir olay işleme temsilcisini bağlamak için başka bir yöntem için, sınıfının yöntemi için kod örneğine bakın <xref:System.Reflection.EventInfo.AddEventHandler%2A> <xref:System.Reflection.EventInfo> .  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Yansımayı kullanarak bir temsilciyi bağlama  
  
1. Olayları başlatan bir tür içeren bir derleme yükleyin. Derlemeler genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemiyle yüklenir. Bu örneği basit tutmak için geçerli derlemede bulunan türetilmiş bir form kullanılır, bu nedenle <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntem geçerli derlemeyi yüklemek için kullanılır.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. <xref:System.Type>Türü temsil eden bir nesne alın ve türün bir örneğini oluşturun. <xref:System.Activator.CreateInstance%28System.Type%29>Yöntemi, parametresiz bir oluşturucuya sahip olduğu için aşağıdaki kodda kullanılır. <xref:System.Activator.CreateInstance%2A>Oluşturmakta olduğunuz türün parametresiz bir Oluşturucusu yoksa kullanabileceğiniz daha fazla başka aşırı yükleme yöntemi vardır. Yeni örnek, <xref:System.Object> derleme hakkında hiçbir şeyin bilinmediğini belirten derlemeyi sürdürmek için tür olarak depolanır. (Yansıma, adlarını önceden bilmeden bir derlemede almanızı sağlar.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. <xref:System.Reflection.EventInfo>Olayı temsil eden bir nesne alın ve <xref:System.Reflection.EventInfo.EventHandlerType%2A> olayı işlemek için kullanılan temsilcinin türünü almak için özelliğini kullanın. Aşağıdaki kodda, <xref:System.Reflection.EventInfo> olay için bir elde edilir <xref:System.Windows.Forms.Control.Click> .  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. <xref:System.Reflection.MethodInfo>Olayı işleyen yöntemi temsil eden bir nesne alır. Bu konunun ilerleyen kısımlarında örnek bölümünde yer alan tüm program kodu, olayı işleyen temsilcinin imzasıyla eşleşen bir yöntemi içerir <xref:System.EventHandler> <xref:System.Windows.Forms.Control.Click> , ancak çalışma zamanında dinamik yöntemler de oluşturabilirsiniz. Ayrıntılar için, dinamik bir yöntem kullanarak çalışma zamanında olay işleyicisi oluşturmak için eşlik eden yordama bakın.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Yöntemini kullanarak temsilcinin bir örneğini oluşturun <xref:System.Delegate.CreateDelegate%2A> . Bu Yöntem statiktir ( `Shared` Visual Basic), bu nedenle temsilci türü sağlanmalıdır. ' <xref:System.Delegate.CreateDelegate%2A> A sahip olan aşırı yüklemelerin kullanılması <xref:System.Reflection.MethodInfo> önerilir.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. `add`Erişimci yöntemini alın ve olayı bağlamak için çağırın. Tüm olayların `add` `remove` , üst düzey dillerin sözdizimi tarafından gizlenen bir erişimcisi ve erişimcisi vardır. Örneğin, C# `+=` olayları bağlamak için Işlecini kullanır ve Visual Basic [AddHandler ifadesini](../../visual-basic/language-reference/statements/addhandler-statement.md)kullanır. Aşağıdaki kod, `add` olayın erişimcisini alır <xref:System.Windows.Forms.Control.Click> ve temsilci örneğini geçirerek geç sınırı çağırır. Bağımsız değişkenlerin bir dizi olarak geçirilmesi gerekir.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu gösterir. Forma tıklanması olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Çalışma zamanında dinamik bir yöntem kullanarak olay işleyicisi oluşturmak için  
  
1. Olay işleyici yöntemleri, basit dinamik yöntemler ve yansıma yayma kullanılarak çalışma zamanında oluşturulabilir. Bir olay işleyicisi oluşturmak için temsilcinin dönüş türü ve parametre türlerine ihtiyacınız vardır. Bu, temsilcinin yöntemi incelenerek elde edilebilir `Invoke` . Aşağıdaki kod, `GetDelegateReturnType` `GetDelegateParameterTypes` Bu bilgileri elde etmek için ve yöntemlerini kullanır. Bu yöntemlerin kodu, bu konunun ilerleyen kısımlarında örnek bölümünde bulunabilir.  
  
     Bir adı vermek gerekli değildir, bu <xref:System.Reflection.Emit.DynamicMethod> nedenle boş dize kullanılabilir. Aşağıdaki kodda, son bağımsız değişken dinamik yöntemi geçerli türle ilişkilendirir ve bu temsilci, sınıfın tüm ortak ve özel üyelerine erişim sağlar `Example` .  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Bir yöntem gövdesi oluşturun. Bu yöntem bir dize yükler, bir dizeyi alan metodun aşırı yüklemesini çağırır, <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> dönüş değerini yığından kapatır (işleyicinin dönüş türü olmadığından) ve döndürür. Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz. [nasıl yapılır: tanımlama ve yürütme dinamik yöntemleri](how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Yöntemini çağırarak dinamik metodu doldurun <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> . `add`Olayın çağırma listesine temsilciyi eklemek için erişimcisini kullanın.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu yükler. Formu tıklatmak, hem önceden tanımlanmış olay işleyicisini hem de yayınlanan olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, var olan bir yöntemin yansıma kullanarak bir olaya nasıl bağlanacağını ve ayrıca, <xref:System.Reflection.Emit.DynamicMethod> çalışma zamanında bir yöntemi göstermek ve bir olaya bağlamak için sınıfını nasıl kullanacağınızı gösterir.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme](how-to-define-and-execute-dynamic-methods.md)
- [Yansıma](reflection.md)
