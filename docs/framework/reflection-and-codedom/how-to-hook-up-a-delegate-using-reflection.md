---
title: 'Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama'
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
ms.openlocfilehash: d748d9f8bdd0b4d831880548d4aceb1c77a0b0c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180499"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama
Yansımayı derlemeleri yüklemek ve çalıştırmak için kullandığınızda, olayları `+=` bağlamak için C# işleci veya Visual Basic [AddHandler deyimi](../../visual-basic/language-reference/statements/addhandler-statement.md) gibi dil özelliklerini kullanamazsınız. Aşağıdaki yordamlar, yansıma yoluyla gerekli tüm türleri alarak varolan bir yöntemi bir olaya nasıl bağlanıncayabildiğini ve yansıma yakılmasını kullanarak dinamik bir yöntem oluşturmanın ve bir olaya nasıl bağlanılacak olduğunu gösterir.  
  
> [!NOTE]
> Olay işleme temsilcisini bağlamanın başka bir yolu için, <xref:System.Reflection.EventInfo.AddEventHandler%2A> <xref:System.Reflection.EventInfo> sınıfın yöntemi için kod örneğine bakın.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Yansımayı kullanarak bir temsilciyi bağlamak için  
  
1. Olayları yükselten bir tür içeren bir derleme yükleyin. Derlemeler genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemle yüklenir. Bu örneği basit tutmak için, geçerli derlemede türetilmiş bir form kullanılır, bu nedenle <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntem geçerli derlemeyi yüklemek için kullanılır.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Türü <xref:System.Type> temsil eden bir nesne alın ve türün bir örneğini oluşturun. Formun parametresiz bir oluşturucusu olduğundan <xref:System.Activator.CreateInstance%28System.Type%29> yöntem aşağıdaki kodda kullanılır. Oluşturduğunuz tür parametresiz <xref:System.Activator.CreateInstance%2A> bir oluşturucu yoksa kullanabileceğiniz yöntemin birkaç diğer aşırı yükleri vardır. Yeni örnek, derleme hakkında <xref:System.Object> hiçbir şeyin bilinmediğini kurgulamak için tür olarak depolanır. (Yansıma önceden adlarını bilmeden bir derleme de türleri almak için izin verir.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Olayı <xref:System.Reflection.EventInfo> temsil eden bir nesne alın <xref:System.Reflection.EventInfo.EventHandlerType%2A> ve olayı işlemek için kullanılan temsilci türünü almak için özelliği kullanın. Aşağıdaki kodda, <xref:System.Reflection.EventInfo> <xref:System.Windows.Forms.Control.Click> olay için bir elde edilir.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Olayı <xref:System.Reflection.MethodInfo> işleyen yöntemi temsil eden bir nesne alın. Bu konunun ilerleyen bölümlerindeki Örnek bölümündeki tam program kodu, <xref:System.EventHandler> <xref:System.Windows.Forms.Control.Click> olayı işleyen temsilcinin imzasıyla eşleşen bir yöntem içerir, ancak çalışma zamanında dinamik yöntemler de oluşturabilirsiniz. Ayrıntılar için, dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için eşlik eden yordamı bakın.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Yöntemi kullanarak temsilcinin bir <xref:System.Delegate.CreateDelegate%2A> örneğini oluşturun. Bu yöntem statiktir (Visual`Shared` Basic'te), bu nedenle temsilci türü sağlanmalıdır. Bu almak aşırı <xref:System.Delegate.CreateDelegate%2A> <xref:System.Reflection.MethodInfo> yükleri kullanarak tavsiye edilir.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Erişimci `add` yöntemini alın ve olayı bağlamak için çağırın. Tüm olayların `add` bir erişimcisi `remove` ve bir erişimcisi vardır ve bunlar üst düzey dillerin sözdizimi tarafından gizlenir. Örneğin, C# olayları `+=` bağlamak için işleci kullanır ve Visual Basic [AddHandler deyimini](../../visual-basic/language-reference/statements/addhandler-statement.md)kullanır. Aşağıdaki kod `add` <xref:System.Windows.Forms.Control.Click> etkinliğin erişimini alır ve temsilci örneğinde geç geç, onu çağırır. Bağımsız değişkenler bir dizi olarak geçirilmelidir.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu gösterir. Formu tıklattığınızda olay işleyicisi çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için  
  
1. Olay işleyici yöntemleri, hafif dinamik yöntemler ve yansıma yayan kullanılarak çalışma zamanında oluşturulabilir. Olay işleyicisi oluşturmak için, temsilcinin dönüş türü ve parametre türlerine ihtiyacınız vardır. Bunlar, temsilcinin `Invoke` yöntemi incelenerek elde edilebilir. Aşağıdaki kod, `GetDelegateReturnType` bu `GetDelegateParameterTypes` bilgileri elde etmek için yöntemleri ve yöntemleri kullanır. Bu yöntemlerin kodu daha sonra bu konuda Örnek bölümünde bulunabilir.  
  
     Boş dize kullanılabilir, <xref:System.Reflection.Emit.DynamicMethod>böylece bir , bir adlandırma gerekli değildir. Aşağıdaki kodda, son bağımsız değişken dinamik yöntemi geçerli türle ilişkilendirerek temsilciye `Example` sınıfın tüm ortak ve özel üyelerine erişim verir.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Bir yöntem gövdesi oluşturun. Bu yöntem bir dize yükler, <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> dize alan yöntemin aşırı yüklenmesini çağırır, yığından geri dönüş değerini çıkarır (işleyicinin dönüş türü olmadığından) ve döndürür. Dinamik yöntemler yayma hakkında daha fazla bilgi edinmek [için bkz.](how-to-define-and-execute-dynamic-methods.md)  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Yöntemini çağırarak dinamik <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi tamamlayın. Olay `add` için çağırma listesine temsilci eklemek için aksesuarı kullanın.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Olayı test edin. Aşağıdaki kod, kod örneğinde tanımlanan formu yükler. Formu tıklattığınızda hem önceden tanımlanmış olay işleyicisi hem de yayılan olay işleyicisi çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, varolan bir yöntemi yansımayı kullanarak bir olaya nasıl <xref:System.Reflection.Emit.DynamicMethod> bağlayın ve ayrıca çalışma zamanında bir yöntem yaydı ve bir olaya bağlamak için sınıfın nasıl kullanılacağını gösterir.  
  
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
