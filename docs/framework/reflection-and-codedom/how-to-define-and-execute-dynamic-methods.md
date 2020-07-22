---
title: 'Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme'
description: Bkz. .NET 'te dinamik yöntemleri tanımlama ve yürütme. Basit bir dinamik yöntemin örneklerini ve bir sınıfının örneğine bağlantılı dinamik bir yöntemi görüntüleyin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
ms.openlocfilehash: 7c68be91deb59ea9439e81561f50b7cc40766a45
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865118"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme
Aşağıdaki yordamlarda basit bir dinamik yöntemin ve bir sınıfının örneğine bağlantılı dinamik yöntemin nasıl tanımlanacağı ve yürütüleceği gösterilmektedir. Dinamik yöntemler hakkında daha fazla bilgi için bkz <xref:System.Reflection.Emit.DynamicMethod> . sınıf ve [yansıma yayma dinamik yöntem senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Dinamik bir yöntemi tanımlamak ve yürütmek için  
  
1. Yöntemi yürütmek için bir temsilci türü bildirin. Bildirmeniz gereken temsilci türü sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün. Aşağıdaki kod, yöntemi için kullanılabilecek iki temsilci türü bildirir `SquareIt` ve bunlardan biri geneldir.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. Dinamik yöntemin parametre türlerini belirten bir dizi oluşturun. Bu örnekte, tek parametre bir `int` ( `Integer` Visual Basic içinde) olduğundan, dizide yalnızca bir öğe vardır.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. Oluşturun <xref:System.Reflection.Emit.DynamicMethod> . Bu örnekte, yöntemi adlandırılır `SquareIt` .  
  
    > [!NOTE]
    > Dinamik yöntem adları vermek gerekli değildir ve ad ile çağrılamaz. Birden çok dinamik yöntem aynı ada sahip olabilir. Ancak, ad çağrı yığınlarında görünür ve hata ayıklama için yararlı olabilir.  
  
     Dönüş değerinin türü olarak belirtilir `long` . Yöntemi, `Example` örnek kodu içeren sınıfını içeren modülle ilişkilendirilir. Yüklü herhangi bir modül belirtilebilir. Dinamik yöntem bir modül düzeyi Yöntem gibi davranır `static` ( `Shared` Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. Yöntem gövdesini yay. Bu örnekte, <xref:System.Reflection.Emit.ILGenerator> Microsoft ara dili (MSIL) oluşturmak için bir nesnesi kullanılır. Alternatif olarak, <xref:System.Reflection.Emit.DynamicILInfo> bir nesnesi, bir için yöntem gövdesini göstermek için yönetilmeyen kod oluşturucularıyla birlikte kullanılabilir <xref:System.Reflection.Emit.DynamicMethod> .  
  
     Bu örnekteki MSIL, bir olan bağımsız değişkeni, `int` yığın üzerine dönüştürür, bir öğesine dönüştürür, `long` çoğaltır `long` ve iki sayıyı çarpar. Bu, kare sonucunu yığında bırakır ve tüm yöntemler döndürülür.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. Yöntemini çağırarak Dynamic metodunu temsil eden temsilcinin bir örneğini (adım 1 ' de belirtilen) oluşturun <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> . Temsilcinin oluşturulması yöntemi tamamlar ve yöntemi değiştirme girişimleri (örneğin, daha fazla MSIL ekleme) yok sayılır. Aşağıdaki kod, bir genel temsilci kullanarak temsilciyi oluşturur ve çağırır.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Bir nesneye bağlanan dinamik bir yöntemi tanımlamak ve yürütmek için  
  
1. Yöntemi yürütmek için bir temsilci türü bildirin. Bildirmeniz gereken temsilci türü sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün. Aşağıdaki kod, bir parametre ve dönüş değeri ile herhangi bir yöntemi yürütmek için kullanılabilen genel bir temsilci türü bildirir veya temsilci bir nesneye bağlıysa iki parametreli bir yöntem ve dönüş değeri döndürür.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. Dinamik yöntemin parametre türlerini belirten bir dizi oluşturun. Yöntemi temsil eden temsilci bir nesneye bağlanmazsa, ilk parametrenin temsilcinin bağlandığı türle eşleşmesi gerekir. Bu örnekte, türü `Example` ve türü `int` (Visual Basic) olmak üzere iki parametre vardır `Integer` .  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. Oluşturun <xref:System.Reflection.Emit.DynamicMethod> . Bu örnekte, yöntemin adı yoktur. Dönüş değerinin türü `int` ( `Integer` Visual Basic) olarak belirtilir. Yöntemi, sınıfının özel ve korunan üyelerine erişebilir `Example` .  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. Yöntem gövdesini yay. Bu örnekte, <xref:System.Reflection.Emit.ILGenerator> Microsoft ara dili (MSIL) oluşturmak için bir nesnesi kullanılır. Alternatif olarak, <xref:System.Reflection.Emit.DynamicILInfo> bir nesnesi, bir için yöntem gövdesini göstermek için yönetilmeyen kod oluşturucularıyla birlikte kullanılabilir <xref:System.Reflection.Emit.DynamicMethod> .  
  
     Bu örnekteki MSIL, sınıfının bir örneği olan ilk bağımsız değişkeni yükler `Example` ve onu türünde bir özel örnek alanının değerini yüklemek için kullanır `int` . İkinci bağımsız değişken yüklenir ve iki sayı çarpılır. Sonuç şundan büyükse `int` , değer kesilir ve en önemli bitler atılır. Yöntemi, yığın üzerinde dönüş değeri ile döndürür.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. Yöntem aşırı yüklemesini çağırarak Dynamic metodunu temsil eden temsilcinin bir örneğini (adım 1 ' de belirtilen) oluşturun <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> . Temsilcinin oluşturulması yöntemi tamamlar ve yöntemi değiştirme girişimleri (örneğin, daha fazla MSIL ekleme) yok sayılır.  
  
    > [!NOTE]
    > <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A>Hedef türün diğer örneklerine bağlantılı temsilciler oluşturmak için yöntemi birden çok kez çağırabilirsiniz.  
  
     Aşağıdaki kod, `Example` özel test alanı 42 olarak ayarlanan sınıfın yeni bir örneğine yöntemini bağlar. Diğer bir deyişle, temsilcinin her çağrıldığı her seferinde `Example` yönteminin ilk parametresine geçirilir.  
  
     `OneParameter`Yöntemin ilk parametresi her zaman örneğini aldığından, temsilci kullanılır `Example` . Temsilci çağrıldığında yalnızca ikinci parametre gereklidir.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir sınıfının örneğine bağlantılı basit bir dinamik yöntemi ve dinamik bir yöntemi gösterir.  
  
 Basit dinamik yöntem bir bağımsız değişken alır, 32 bitlik bir tamsayıdır ve bu tamsayının 64 bit karesini döndürür. Yöntemi çağırmak için genel bir temsilci kullanılır.  
  
 İkinci dinamik yöntemin türü `Example` ve türü `int` (Visual Basic) olmak üzere iki parametresi vardır `Integer` . Dinamik yöntem oluşturulduğunda, `Example` türünde bir bağımsız değişkenine sahip olan genel bir temsilci kullanarak bir örneğine bağlanır `int` . `Example`Yöntemin ilk parametresi her zaman ' ın bağlantılı örneğini aldığından, temsilcinin türünde bir bağımsız değişkeni yoktur `Example` . Temsilci çağrıldığında yalnızca `int` bağımsız değişken sağlanır. Bu dinamik yöntem, sınıfının özel bir alanına erişir `Example` ve özel alanın ve `int` bağımsız değişkenin çarpımını döndürür.  
  
 Kod örneği, yöntemleri yürütmek için kullanılabilecek temsilcileri tanımlar.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.DynamicMethod>
- [Yansıma yayma kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Yansıma yayma dinamik yöntem senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))
