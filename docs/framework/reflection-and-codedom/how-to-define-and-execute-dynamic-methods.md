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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17bc7c417980c0850788f082ebb6e810fd0c53d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793243"
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme
Aşağıdaki yordamlar tanımlama ve basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı olarak dinamik bir yöntem yürütme işlemini göstermektedir. Dinamik yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve [yansıma yayma dinamik yöntem senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100)).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Dinamik bir yöntem tanımlayıp  
  
1. Metodunu yürütmek için bir temsilci türü bildirin. Genel temsilci bildirmenize gerek temsilci türleri sayısını en aza indirmek için kullanmayı düşünün. Aşağıdaki kod türleri için kullanılabilecek iki temsilci bildirir `SquareIt` yöntemi ve bunlardan birinin geneldir.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2. Dinamik yöntem için parametre türlerini belirten bir dizi oluşturun. Bu örnekte, yalnızca bir parametresi olan bir `int` (`Integer` Visual Basic'te), yalnızca bir öğe dizisi sahiptir.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3. Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>. Bu örnekte, yöntem adlı `SquareIt`.  
  
    > [!NOTE]
    >  Dinamik yöntemler adlar vermek gerekli değildir ve ada göre çağrılamaz. Birden çok dinamik yöntem aynı ada sahip olabilir. Ancak, ad çağrı yığınlarıyla görüntülenir ve hata ayıklama için yararlı olabilir.  
  
     Dönüş değerinin türü olarak belirtilen `long`. İçeren modül ile ilişkili bir yöntemdir `Example` örnek kod içeren sınıf. Yüklenen bir modülün belirtilebilir. Dinamik yöntem gibi davranır, yalnızca bir modül düzeyinde `static` yöntemi (`Shared` Visual Basic'te).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4. Yöntem gövdesini gösterin. Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dilini (MSIL) göstermek için kullanılır. Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesini yaymak için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Bu örnekte MSIL olan bağımsız değişkeni yükleyen bir `int`, yığın üstüne dönüştürür bir `long`, yinelenenleri `long`ve iki sayıyı çarpar. Bu kare sonucu yığında bırakır ve dönüş tüm yöntemi yapması gerekir.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5. Dinamik yöntem çağırarak temsil eden bir (1. adımda belirtilen) temsilci örneğini oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi. Temsilci oluşturma yöntemi tamamlandıktan ve herhangi ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir. Aşağıdaki kod, temsilci oluşturur ve bu, Genel temsilci kullanarak çağırır.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Bir nesneye bağımlı dinamik bir yöntem tanımlayıp  
  
1. Metodunu yürütmek için bir temsilci türü bildirin. Genel temsilci bildirmenize gerek temsilci türleri sayısını en aza indirmek için kullanmayı düşünün. Aşağıdaki kod, temsilci bir nesneye bağlıysa, herhangi bir yöntemle bir parametre ve dönüş değeri veya iki parametre ile bir yöntem ve bir dönüş değeri yürütmek için kullanılan genel temsilci türünde bildirir.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2. Dinamik yöntem için parametre türlerini belirten bir dizi oluşturun. Yöntemi temsil eden bir temsilci bir nesneye bağlı ise, ilk parametresinin temsilci bağlı türüyle eşleşmelidir. Bu örnekte, türünün iki parametresi vardır `Example` ve türü `int` (`Integer` Visual Basic'te).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3. Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>. Bu örnekte, yöntem adı yok. Dönüş değerinin türü olarak belirtilen `int` (`Integer` Visual Basic'te). Yöntem özel ve korumalı üyelerine erişebilir `Example` sınıfı.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4. Yöntem gövdesini gösterin. Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dilini (MSIL) göstermek için kullanılır. Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesini yaymak için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Bu örnekte MSIL bir örneği olan ilk bağımsız değişken, yükler, `Example` sınıfı ve türü özel örnek alanı değerini yüklemek için kullandığı `int`. İkinci bağımsız değişkeni yüklenir ve iki sayı çarpılır. Sonucu daha büyük ise `int`, değer kesilir ve en önemli bitleri atılır. Yöntemi, yığında dönüş değeri döndürür.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5. Dinamik yöntem çağırarak temsil eden bir (1. adımda belirtilen) temsilci örneğini oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> yöntemi aşırı yüklemesi. Temsilci oluşturma yöntemi tamamlandıktan ve herhangi ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir.  
  
    > [!NOTE]
    >  Çağırabilirsiniz <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi hedef türünün diğer örneklerine bağlı temsilci oluşturmak için birden çok kez.  
  
     Aşağıdaki kod yöntemi yeni bir örneğine bağlanır `Example` sınıfı olan özel test alan, 42'ye ayarlanır. Diğer bir deyişle, her zaman temsilci örneğini çağrılan `Example` yöntemin ilk parametre olarak geçirilir.  
  
     Temsilci `OneParameter` yönteminin ilk parametresi her zaman örneği aldığından kullanılan `Example`. Temsilci çağrıldığında, yalnızca ikinci parametresi gereklidir.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı olarak dinamik bir yöntem gösterilmektedir.  
  
 Basit bir dinamik yöntem, tek bir bağımsız değişken bir 32 bit tamsayı ve tamsayıyı 64-bit karesini döndürür. Genel temsilci yöntemini çağırmak için kullanılır.  
  
 İkinci bir dinamik yöntem türünde iki parametre sahip `Example` ve türü `int` (`Integer` Visual Basic'te). Dinamik yöntem oluşturulduğunda bir örneğine bağlanır `Example`, bir bağımsız değişken türü olan genel temsilci kullanarak `int`. Temsilci türünde bir bağımsız değişken yok `Example` yönteminin ilk parametresi her zaman bağlı örneğini aldığından `Example`. Ne zaman temsilcisi çağrıldığında, yalnızca `int` bağımsız değişken sağlanır. Bu dinamik yöntem, özel bir alan erişen `Example` sınıfı ve özel alan çarpımını döndürür ve `int` bağımsız değişken.  
  
 Kod örneği, yöntemi yürütmek için kullanılan temsilci tanımlar.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
- Hiçbir ek derleme başvurularını gereklidir.  
  
- Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.DynamicMethod>
- [Yansıma yaymanın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Yansıma yayma dinamik yöntem senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sfk2s47t(v=vs.100))
