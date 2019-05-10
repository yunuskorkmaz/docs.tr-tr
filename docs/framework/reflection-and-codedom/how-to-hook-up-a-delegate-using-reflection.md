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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bc4b4df6829f5b86dff400c5cd7cbd3d86f5507
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591540"
---
# <a name="how-to-hook-up-a-delegate-using-reflection"></a>Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama
Yansıma yüklemek ve derlemeleri çalıştırmak için kullandığınız zaman gibi dil özellikleri kullanamazsınız C# `+=` işleci veya Visual Basic [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md) olayları yeteneklerinizi. Aşağıdaki yordamlar, gerekli tüm türlerin yansıma yoluyla alarak bir olay için varolan bir yöntem denetime nasıl gösterir ve yansıma kullanarak dinamik bir yöntem oluşturma yayma ve en fazla olay bağlama.  
  
> [!NOTE]
>  Kod örneği için bir olay işleme temsilci bağlama başka bir yol için bkz <xref:System.Reflection.EventInfo.AddEventHandler%2A> yöntemi <xref:System.Reflection.EventInfo> sınıfı.  
  
### <a name="to-hook-up-a-delegate-using-reflection"></a>Yansıma kullanarak temsilci bağlama için  
  
1. Olayları oluşturan bir tür içeren bir bütünleştirilmiş kod yükleme. Derlemeler ile yüklenen genellikle <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi. Bu örneği basit tutmak için geçerli derlemedeki türetilmiş bir form kullanılır, böylece <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> yöntemi geçerli derlemeyi yüklemek için kullanılır.  
  
     [!code-cpp[HookUpDelegate#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#3)]
     [!code-csharp[HookUpDelegate#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#3)]
     [!code-vb[HookUpDelegate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#3)]  
  
2. Alma bir <xref:System.Type> türünü temsil eden nesne ve türün bir örneğini oluşturun. <xref:System.Activator.CreateInstance%28System.Type%29> Biçiminde varsayılan bir oluşturucuya sahip olduğundan aşağıdaki kodda yöntemi kullanılır. Birkaç diğer aşırı yüklemeleri vardır <xref:System.Activator.CreateInstance%2A> oluşturmakta olduğunuz türü varsayılan bir oluşturucuya sahip değilse, kullanabileceğiniz yöntemi. Yeni örnek türü olarak saklanır <xref:System.Object> kurgu korumak için hiçbir şeyin hakkında derleme adı verilir. (Yansıma türlerini adlarını önceden farkında olmadan bir derlemede yararlanmanıza olanak sağlar.)  
  
     [!code-cpp[HookUpDelegate#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#4)]
     [!code-csharp[HookUpDelegate#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#4)]
     [!code-vb[HookUpDelegate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#4)]  
  
3. Alma bir <xref:System.Reflection.EventInfo> olayı temsil eden nesne ve kullanmak <xref:System.Reflection.EventInfo.EventHandlerType%2A> olayı işlemek için kullanılan temsilci türünü alınacağı özellik. Aşağıdaki kodda bir <xref:System.Reflection.EventInfo> için <xref:System.Windows.Forms.Control.Click> olay elde edilir.  
  
     [!code-cpp[HookUpDelegate#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#5)]
     [!code-csharp[HookUpDelegate#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#5)]
     [!code-vb[HookUpDelegate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#5)]  
  
4. Alma bir <xref:System.Reflection.MethodInfo> olayı işleyen yöntemi temsil eden nesne. Örnek bölümünde bu konunun ilerleyen bölümlerinde tam program kodunda imzası eşleşen bir yöntem içerir <xref:System.EventHandler> temsilcisi, yürüten <xref:System.Windows.Forms.Control.Click> olay, ancak aynı zamanda oluşturabileceği dinamik yöntemler çalışma zamanında. Dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için eşlik eden yordamı, Ayrıntılar için bkz.  
  
     [!code-cpp[HookUpDelegate#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#6)]
     [!code-csharp[HookUpDelegate#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#6)]
     [!code-vb[HookUpDelegate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#6)]  
  
5. Kullanarak temsilci örneğini oluşturmak <xref:System.Delegate.CreateDelegate%2A> yöntemi. Bu yöntem statiktir (`Shared` Visual Basic'te), temsilci türü sağlanmalı. Aşırı yüklemeleri kullanılarak <xref:System.Delegate.CreateDelegate%2A> süren bir <xref:System.Reflection.MethodInfo> önerilir.  
  
     [!code-cpp[HookUpDelegate#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#7)]
     [!code-csharp[HookUpDelegate#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#7)]
     [!code-vb[HookUpDelegate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#7)]  
  
6. Alma `add` erişimci yöntemi ve bu olay yeteneklerinizi çağırın. Tüm olayları sahip bir `add` erişimci ve `remove` üst düzey dillerin sözdizimi tarafından gizlenmiş erişimcisi. Örneğin, C# kullanan `+=` olayları ve Visual Basic kullanan yeteneklerinizi işleci [AddHandler deyimi](~/docs/visual-basic/language-reference/statements/addhandler-statement.md). Aşağıdaki kod alır `add` erişimcisine <xref:System.Windows.Forms.Control.Click> olay ve çağırdığı geç temsilci örneğini geçirerek bağlama,. Bağımsız değişken bir dizi olarak geçirilmelidir.  
  
     [!code-cpp[HookUpDelegate#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#8)]
     [!code-csharp[HookUpDelegate#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#8)]
     [!code-vb[HookUpDelegate#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#8)]  
  
7. Olay test edin. Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan bir form gösterir. Form tıklayarak olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
<a name="procedureSection1"></a>   
### <a name="to-generate-an-event-handler-at-run-time-by-using-a-dynamic-method"></a>Dinamik bir yöntem kullanarak çalışma zamanında bir olay işleyicisi oluşturmak için  
  
1. Olay işleyicisi yöntemleri basit dinamik yöntemler kullanarak çalışma zamanında oluşturulabilir ve yansıma yayma. Bir olay işleyicisi oluşturmak için dönüş türü ve parametre türleri temsilci gerekir. Bu temsilcinin inceleyerek alınabilir `Invoke` yöntemi. Aşağıdaki kod `GetDelegateReturnType` ve `GetDelegateParameterTypes` bu bilgileri almak için yöntemleri. Bu yöntemleri için kod, bu konunun ilerleyen bölümlerinde örnek bölümünde bulunabilir.  
  
     Ad için gerekli değil bir <xref:System.Reflection.Emit.DynamicMethod>, bu nedenle boş dize kullanılabilir. Aşağıdaki kodda, dinamik yöntem son bağımsız değişken, temsilci erişimi tüm genel ve özel üyelerine vererek geçerli türü ile ilişkilendirir. `Example` sınıfı.  
  
     [!code-cpp[HookUpDelegate#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#9)]
     [!code-csharp[HookUpDelegate#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#9)]
     [!code-vb[HookUpDelegate#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#9)]  
  
2. Bir yöntem gövdesi oluşturur. Bu yöntem bir dize yükler, aşırı yüklemesini çağırır <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=nameWithType> (işleyicisi yok dönüş türüne sahip olduğundan) yönteminin bir dize alan POP yığından dönüş değeri ve döndürür. Dinamik yöntemleri yayma hakkında daha fazla bilgi için bkz: [nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md).  
  
     [!code-cpp[HookUpDelegate#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#10)]
     [!code-csharp[HookUpDelegate#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#10)]
     [!code-vb[HookUpDelegate#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#10)]  
  
3. Dinamik yöntem çağırarak tamamlamak kendi <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi. Kullanım `add` çağırma listesi olayı için temsilci eklemek için erişimcisi.  
  
     [!code-cpp[HookUpDelegate#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#11)]
     [!code-csharp[HookUpDelegate#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#11)]
     [!code-vb[HookUpDelegate#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#11)]  
  
4. Olay test edin. Aşağıdaki kod, aşağıdaki kod örneğinde tanımlanan formu yükler. Form tıklayarak, önceden tanımlanmış bir olay işleyicisi hem yayılan olay işleyicisini çağırır.  
  
     [!code-cpp[HookUpDelegate#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#12)]
     [!code-csharp[HookUpDelegate#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#12)]
     [!code-vb[HookUpDelegate#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde nasıl yansıma kullanarak bir olay için varolan bir yöntem bağlama ve nasıl kullanılacağını gösterir. <xref:System.Reflection.Emit.DynamicMethod> en fazla olay bağlama ve çalışma zamanında bir yöntem yaymak için sınıf.  
  
 [!code-cpp[HookUpDelegate#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HookUpDelegate/cpp/source.cpp#1)]
 [!code-csharp[HookUpDelegate#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HookUpDelegate/cs/source.cs#1)]
 [!code-vb[HookUpDelegate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HookUpDelegate/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
- Hiçbir ek derleme başvuruları, komut satırından derleme için gereklidir. Bu örnek bir konsol uygulaması olduğundan, Visual Studio'da System.Windows.Forms.dll'e bir başvuru eklemelisiniz.  
  
- Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>
- <xref:System.Reflection.Emit.DynamicMethod>
- <xref:System.Activator.CreateInstance%2A>
- <xref:System.Delegate.CreateDelegate%2A>
- [Nasıl yapılır: Dinamik yöntemleri tanımlama ve yürütme](../../../docs/framework/reflection-and-codedom/how-to-define-and-execute-dynamic-methods.md)
- [Yansıma](../../../docs/framework/reflection-and-codedom/reflection.md)
