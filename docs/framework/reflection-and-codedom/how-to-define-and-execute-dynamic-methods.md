---
title: 'Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
ms.openlocfilehash: 7da9d0bea755b90f73077fcd56558ed66a80e2eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130145"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme
Aşağıdaki yordamlarda basit bir dinamik yöntemin ve bir sınıfının örneğine bağlantılı dinamik yöntemin nasıl tanımlanacağı ve yürütüleceği gösterilmektedir. Dinamik yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve [yansıma yayma dinamik yöntem senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Dinamik bir yöntemi tanımlamak ve yürütmek için  
  
1. Yöntemi yürütmek için bir temsilci türü bildirin. Bildirmeniz gereken temsilci türü sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün. Aşağıdaki kod `SquareIt` yöntemi için kullanılabilecek iki temsilci türü bildirir ve bunlardan biri geneldir.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. Dinamik yöntemin parametre türlerini belirten bir dizi oluşturun. Bu örnekte, tek parametre bir `int` (Visual Basic)`Integer`, bu yüzden dizide yalnızca bir öğe vardır.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. <xref:System.Reflection.Emit.DynamicMethod>oluşturun. Bu örnekte, yöntemi `SquareIt`olarak adlandırılır.  
  
    > [!NOTE]
    > Dinamik yöntem adları vermek gerekli değildir ve ad ile çağrılamaz. Birden çok dinamik yöntem aynı ada sahip olabilir. Ancak, ad çağrı yığınlarında görünür ve hata ayıklama için yararlı olabilir.  
  
     Dönüş değerinin türü `long`olarak belirtilir. Yöntemi, örnek kodu içeren `Example` sınıfını içeren modülle ilişkilendirilir. Yüklü herhangi bir modül belirtilebilir. Dinamik yöntem bir modül düzeyi `static` yöntemi (Visual Basic`Shared`) gibi davranır.  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. Yöntem gövdesini yay. Bu örnekte, Microsoft ara dili (MSIL) oluşturmak için bir <xref:System.Reflection.Emit.ILGenerator> nesnesi kullanılır. Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesnesi, bir <xref:System.Reflection.Emit.DynamicMethod>için yöntem gövdesini yaymak üzere yönetilmeyen kod oluşturucularıyla birlikte kullanılabilir.  
  
     Bu örnekteki MSIL, `int`bağımsız değişkenini yükler, yığın üzerine bir `long`dönüştürür, `long`çoğaltır ve iki sayıyı çarpar. Bu, kare sonucunu yığında bırakır ve tüm yöntemler döndürülür.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemini çağırarak, Dynamic metodunu temsil eden temsilcinin bir örneğini (adım 1 ' de belirtilen) oluşturun. Temsilcinin oluşturulması yöntemi tamamlar ve yöntemi değiştirme girişimleri (örneğin, daha fazla MSIL ekleme) yok sayılır. Aşağıdaki kod, bir genel temsilci kullanarak temsilciyi oluşturur ve çağırır.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Bir nesneye bağlanan dinamik bir yöntemi tanımlamak ve yürütmek için  
  
1. Yöntemi yürütmek için bir temsilci türü bildirin. Bildirmeniz gereken temsilci türü sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün. Aşağıdaki kod, bir parametre ve dönüş değeri ile herhangi bir yöntemi yürütmek için kullanılabilen genel bir temsilci türü bildirir veya temsilci bir nesneye bağlıysa iki parametreli bir yöntem ve dönüş değeri döndürür.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. Dinamik yöntemin parametre türlerini belirten bir dizi oluşturun. Yöntemi temsil eden temsilci bir nesneye bağlanmazsa, ilk parametrenin temsilcinin bağlandığı türle eşleşmesi gerekir. Bu örnekte, `Example` türünde iki parametre vardır ve `int` (`Integer` Visual Basic).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. <xref:System.Reflection.Emit.DynamicMethod>oluşturun. Bu örnekte, yöntemin adı yoktur. Dönüş değerinin türü `int` (`Integer` Visual Basic) olarak belirtilir. Yöntemi, `Example` sınıfının özel ve korunan üyelerine erişebilir.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. Yöntem gövdesini yay. Bu örnekte, Microsoft ara dili (MSIL) oluşturmak için bir <xref:System.Reflection.Emit.ILGenerator> nesnesi kullanılır. Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesnesi, bir <xref:System.Reflection.Emit.DynamicMethod>için yöntem gövdesini yaymak üzere yönetilmeyen kod oluşturucularıyla birlikte kullanılabilir.  
  
     Bu örnekteki MSIL, `Example` sınıfının bir örneği olan ilk bağımsız değişkeni yükler ve `int`türünde bir özel örnek alanının değerini yüklemek için kullanır. İkinci bağımsız değişken yüklenir ve iki sayı çarpılır. Sonuç `int`büyükse, değer kesilir ve en önemli bitler atılır. Yöntemi, yığın üzerinde dönüş değeri ile döndürür.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> yöntemi aşırı yüklemesini çağırarak Dynamic metodunu temsil eden temsilcinin bir örneğini (adım 1 ' de belirtilen) oluşturun. Temsilcinin oluşturulması yöntemi tamamlar ve yöntemi değiştirme girişimleri (örneğin, daha fazla MSIL ekleme) yok sayılır.  
  
    > [!NOTE]
    > Hedef türün diğer örneklerine bağlantılı temsilciler oluşturmak için <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemini birden çok kez çağırabilirsiniz.  
  
     Aşağıdaki kod yöntemi, özel test alanı 42 olarak ayarlanan `Example` sınıfının yeni bir örneğine bağlar. Diğer bir deyişle, temsilcinin her çağrılışında `Example` örneği yöntemin ilk parametresine geçirilir.  
  
     `OneParameter` temsilci, yöntemin ilk parametresi her zaman `Example`örneğini aldığından kullanılır. Temsilci çağrıldığında yalnızca ikinci parametre gereklidir.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir sınıfının örneğine bağlantılı basit bir dinamik yöntemi ve dinamik bir yöntemi gösterir.  
  
 Basit dinamik yöntem bir bağımsız değişken alır, 32 bitlik bir tamsayıdır ve bu tamsayının 64 bit karesini döndürür. Yöntemi çağırmak için genel bir temsilci kullanılır.  
  
 İkinci dinamik yöntemin `Example` türünde iki parametresi vardır ve `int` (`Integer` Visual Basic) yazın. Dinamik yöntem oluşturulduğunda, bir `Example`örneğine bağlanır ve `int`türünde bir bağımsız değişkene sahip olan genel bir temsilci kullanılarak yapılır. Yöntemin ilk parametresi her zaman `Example` bağlantılı `Example`örneğini aldığından, temsilcinin türünde bir bağımsız değişkeni yoktur. Temsilci çağrıldığında yalnızca `int` bağımsız değişkeni sağlanır. Bu dinamik yöntem `Example` sınıfının özel bir alanına erişir ve özel alanın ve `int` bağımsız değişkeninin çarpımını döndürür.  
  
 Kod örneği, yöntemleri yürütmek için kullanılabilecek temsilcileri tanımlar.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.DynamicMethod>
- [Yansıma yayma kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Yansıma yayma dinamik yöntem senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))
