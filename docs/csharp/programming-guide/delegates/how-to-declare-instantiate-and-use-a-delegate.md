---
title: 'Nasıl yapılır: Bildirme, oluşturma ve bir temsilci - kullanın C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 8ecbac4608cfd42aa099a0cd66d7d22241a93265
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557714"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Nasıl yapılır: Bildirme, oluşturma ve bir temsilci kullanın (C# Programlama Kılavuzu)
C# 1.0 ve daha sonra aşağıdaki örnekte gösterildiği gibi temsilciler bildirilebilir.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 C# 2.0 ve sonraki sürümlerinde, ayrıca bildirmek ve başlatmak için anonim bir yöntem kullanmak mümkün bir [temsilci](../../../csharp/language-reference/keywords/delegate.md)aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 C# 3.0 ve sonraki sürümlerinde, temsilciler ayrıca bildirilmiş ve bir lambda ifadesi kullanarak, aşağıdaki örnekte gösterildiği gibi örneği.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki örnek, bir temsilci kullanarak bildirme ve örnekleme gösterir. `BookDB` Sınıfı, bir veritabanına kitap tutan bir Kitaplığı veritabanı kapsüller. Bir yöntem sunan `ProcessPaperbackBooks`, veritabanında kitapları ve her biri için bir temsilci çağıran, tüm alınabilen ciltsiz kitaba bulur. `delegate` Kullanılan türünün adı `ProcessBookDelegate`. `Test` Sınıfı başlıklar ve ortalama fiyat kitapçığın kitap yazdırmak için bu sınıfı kullanır.  
  
 Temsilciler kullanımını işlevselliği Kitaplığı veritabanı ve istemci kodu arasında iyi ayrımı yükseltir. İstemci kodu books nasıl depolandığını veya kitaplığı kod kitapçığın books nasıl bulacağını olanağıyla sahiptir. Kitaplığı kod bunları bulduktan sonra hangi işleme kitapçığın kitaplar yapılır bilgisi var.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
-   Bir temsilci bildirme.  
  
     Aşağıdaki deyim, yeni bir temsilci türü bildirir.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Her bir temsilci türü sayısı ve bağımsız değişken türlerinin ve onu kapsülleyen yöntemleri dönüş değerinin türünü açıklar. Bağımsız değişken türleri ya da dönüş değeri yeni bir dizi gerektiğinde yeni bir temsilci türünün bildirilmesi gerekir.  
  
-   Bir temsilci örneği.  
  
     Bir temsilci türü bildirildikten sonra bir temsilci nesnesinin oluşturulabilir ve belirli bir yöntem ile ilişkili. Önceki örnekte geçirerek bunu `PrintTitle` yönteme `ProcessPaperbackBooks` yöntem aşağıdaki örnekteki gibi:  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Bu yeni bir temsilci nesnesi ile ilişkili oluşturur [statik](../../../csharp/language-reference/keywords/static.md) yöntemi `Test.PrintTitle`. Benzer şekilde, statik olmayan yöntemi `AddBookToTotal` nesnesindeki `totaller` aşağıdaki örnekte olduğu gibi geçirilir:  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     Her iki durumda da yeni bir temsilci nesnesi için geçirilen `ProcessPaperbackBooks` yöntemi.  
  
     Yöntemi daha temsilci oluşturduktan sonra bile asla değişikliklerle ilişkili; temsilci nesneleri sabittir.  
  
-   Bir temsilci çağırma.  
  
     Bir temsilci nesne oluşturulduktan sonra temsilci nesne temsilci çağıran başka bir kod için genellikle geçirilir. Bir temsilci nesnesinin temsilciye geçirilecek parantez içine alınmış bağımsız değişkenleri ardından temsilci nesnesinin adı kullanılarak çağrılır. Bir temsilci çağrısının bir örneği verilmiştir:  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Bir temsilci ya da zaman uyumlu olarak, bu örnekte olduğu gibi veya zaman uyumsuz olarak kullanarak çağrılabilir `BeginInvoke` ve `EndInvoke` yöntemleri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
