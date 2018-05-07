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
ms.openlocfilehash: 53142ffa38bda036dd558dd6d23912ebd2e393ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>Nasıl yapılır: Dinamik Yöntemleri Tanımlama ve Yürütme
Aşağıdaki yordamlar, tanımlayın ve basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı dinamik yöntemi yürütme gösterilmektedir. Dinamik yöntemleri hakkında daha fazla bilgi için bkz: <xref:System.Reflection.Emit.DynamicMethod> sınıfı ve [yansıma yayma dinamik yöntemi senaryoları](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>Dinamik bir yöntem yürütülmeye ve tanımlamak için  
  
1.  Execute yöntemi için bir temsilci türü bildirin. Temsilci türleri bildirmeniz gerekir sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün. Aşağıdaki kod, iki temsilci için kullanılabilir türleri bildirir `SquareIt` yöntemi ve bunlardan biri genel.  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  Dinamik yöntemi için parametre türleri belirten bir dizi oluşturun. Bu örnekte, yalnızca parametredir bir `int` (`Integer` Visual Basic'te), dizi yalnızca tek bir öğe içeriyor.  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>. Bu örnekte, yöntem adlı `SquareIt`.  
  
    > [!NOTE]
    >  Dinamik yöntemler adlar vermek gerekli değildir ve ada göre çağrılamaz. Birden çok dinamik yöntemleri aynı ada sahip olabilir. Ancak, ad içinde çağrı yığınları görünür ve hata ayıklama için yararlı olabilir.  
  
     Dönüş değeri türü olarak belirtildiğinde `long`. İçeren modülü ile ilişkili bir yöntemdir `Example` örnek kodu içeren sınıf. Herhangi bir yüklenen modül belirtilebilir. Modül düzeyi gibi dinamik yöntemi davranır `static` yöntemi (`Shared` Visual Basic'te).  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  Yöntem gövdesi yayma. Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dili (MSIL) yaymak üzere kullanılır. Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesi yayma için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Bu örnekte MSIL olan bağımsız değişkeni yükler bir `int`, yığına dönüştürür bir `long`, yinelenen `long`ve iki sayının çoğaltır. Bu squared sonuç yığında bırakır ve dönüş tüm yapmak için yöntem vardır.  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  Dinamik yöntemini çağırarak temsil eden örnek (1. adımda bildirilen) temsilcisi oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi. Temsilci oluşturma yöntemi tamamlar ve herhangi bir ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir. Aşağıdaki kod temsilci oluşturur ve onu, genel bir temsilci kullanarak çağırır.  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>Nesneye bağlı dinamik bir yöntem yürütülmeye ve tanımlamak için  
  
1.  Execute yöntemi için bir temsilci türü bildirin. Temsilci türleri bildirmeniz gerekir sayısını en aza indirmek için genel bir temsilci kullanmayı düşünün. Aşağıdaki kod, bir nesneye temsilci bağlıysa herhangi bir yöntemle bir parametre ve dönüş değeri veya iki parametrelere sahip bir yöntem ve dönüş değeri yürütmek için kullanılan bir genel temsilci türü bildirir.  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  Dinamik yöntemi için parametre türleri belirten bir dizi oluşturun. Yöntemi temsil eden temsilci nesneye bağlı ise, ilk parametre temsilci bağlı türüyle eşleşmelidir. Bu örnekte, türünde iki parametre vardır `Example` ve türü `int` (`Integer` Visual Basic'te).  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  Oluşturma bir <xref:System.Reflection.Emit.DynamicMethod>. Bu örnekte, yöntem adı yok. Dönüş değeri türü olarak belirtildiğinde `int` (`Integer` Visual Basic'te). Yöntemi özel ve korumalı üye erişimi `Example` sınıfı.  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  Yöntem gövdesi yayma. Bu örnekte, bir <xref:System.Reflection.Emit.ILGenerator> nesnesi, Microsoft Ara dili (MSIL) yaymak üzere kullanılır. Alternatif olarak, bir <xref:System.Reflection.Emit.DynamicILInfo> nesne birlikte ile yönetilmeyen kod oluşturucuları için yöntem gövdesi yayma için kullanılabilir bir <xref:System.Reflection.Emit.DynamicMethod>.  
  
     Bir örneği olan ilk bağımsız değişkeni, bu örnekte MSIL yükler, `Example` sınıfı ve türünde bir özel örneği alan değeri yüklemek için kullandığı `int`. İkinci bağımsız değişkeni yüklenir ve iki sayının çarpılmasıyla hesaplanır. Sonuç daha büyük ise `int`, değer kesilir ve en önemli BITS atılır. Yöntemi, yığında dönüş değeri döndürür.  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  Dinamik yöntemini çağırarak temsil eden örnek (1. adımda bildirilen) temsilcisi oluşturmak <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> yöntemi aşırı yüklemesini. Temsilci oluşturma yöntemi tamamlar ve herhangi bir ek çalışır yöntemini değiştirmek — örneğin, daha fazla MSIL ekleme — göz ardı edilir.  
  
    > [!NOTE]
    >  Çağırabilirsiniz <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> yöntemi birden çok kez hedef türü diğer örneklerine bağlı temsilciler oluşturmak için.  
  
     Aşağıdaki kod yöntemi yeni bir örneğine bağlar `Example` sınıfı olan özel bir test alan 42'ye ayarlanır. Diğer bir deyişle, her zaman temsilci örneğini çağrılan `Example` yöntemi ilk parametre olarak geçirilir.  
  
     Temsilci `OneParameter` yönteminin ilk parametresi her zaman örneğini aldığından kullanılan `Example`. Temsilci çağrıldığında, yalnızca ikinci parametresi gereklidir.  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, basit bir dinamik yöntem ve bir sınıfın bir örneğine bağlı dinamik bir yöntemi gösterir.  
  
 Basit dinamik yöntemi tek bir bağımsız değişken bir 32 bit tamsayı ve 64-bit tamsayıyı karesini verir. Genel temsilci yöntemini çağırmak için kullanılır.  
  
 İkinci dinamik yöntemi türü iki parametreye sahip `Example` ve türü `int` (`Integer` Visual Basic'te). Dinamik yöntemi oluşturduğunuzda bir örneğine bağlanır `Example`, türünde bir bağımsız değişken sahip genel bir temsilci kullanarak `int`. Temsilci türünde bir bağımsız değişken yok `Example` yönteminin ilk parametresi her zaman bağlı örneğini aldığından `Example`. Ne zaman temsilci çağrılır, yalnızca `int` bağımsız değişkeni sağlanmaktadır. Dinamik bu yöntem, özel bir alan erişir `Example` sınıfı ve özel alan çarpımını döndürür ve `int` bağımsız değişkeni.  
  
 Kod örneği yöntemleri yürütmek için kullanılan temsilciler tanımlar.  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını gereklidir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [Yansıma kullanarak yayma](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Yansıma yayma dinamik yöntemi senaryoları](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
