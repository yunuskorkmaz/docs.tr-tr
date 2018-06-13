---
title: 'Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], declaring and instantiating
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
ms.openlocfilehash: 19e5883135d65a648bb6afb74a475b761f572a95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333979"
---
# <a name="how-to-declare-instantiate-and-use-a-delegate-c-programming-guide"></a>Nasıl yapılır: Temsilci Bildirme, Oluşturma ve Kullanma (C# Programlama Kılavuzu)
C# 1.0 ve daha sonra aşağıdaki örnekte gösterildiği gibi temsilciler bildirilebilir.  
  
 [!code-csharp[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C# 2.0, aşağıdaki örnekte gösterildiği gibi önceki bildirimi yazmak için daha basit bir yol sağlar.  
  
 [!code-csharp[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 C# 2.0 ve daha sonra aynı zamanda adsız bir yöntem bildirin ve başlatmak için kullanmak mümkün bir [temsilci](../../../csharp/language-reference/keywords/delegate.md), aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 C# 3.0 ve sonraki sürümlerinde, temsilciler ayrıca bildirilmiş ve bir lambda ifadesi kullanarak aşağıdaki örnekte gösterildiği gibi örneği.  
  
 [!code-csharp[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Aşağıdaki örnek, bir temsilci kullanarak bildirme ve örnek oluşturma gösterilmektedir. `BookDB` Sınıfı defterleri bir veritabanının bakımını yapan bir kitap veritabanı yalıtır. Bir yöntemi gösterir `ProcessPaperbackBooks`, veritabanında defterleri, tüm paperback bulur ve her biri için bir temsilcisini çağırır. `delegate` Kullanılan türünü adlandırılan `ProcessBookDelegate`. `Test` Sınıfı başlıklarını ve ortalama fiyat kitapçığın defterlerinden yazdırmak için bu sınıfı kullanır.  
  
 Temsilciler kullanımını işlevselliği kitap veritabanı ve istemci kodu arasında iyi ayrılması yükseltir. İstemci kodu books nasıl depolandığını veya Kitap kod kitapçığın books nasıl bulacağını olanağıyla sahiptir. Kitap kod bunları bulduktan sonra hangi işleme kitapçığın books üzerinde gerçekleştirilir hiçbir bilgiye sahiptir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
-   Bir temsilci bildirme.  
  
     Aşağıdaki ifade, yeni bir temsilci türü bildirir.  
  
     [!code-csharp[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     Her bir temsilci türü sayısı ve bağımsız değişken türleri ve onu sarmalayabilen yöntemleri dönüş değerini türünü açıklar. Yeni bir bağımsız değişken türleri veya dönüş değeri türü kümesi gerektiğinde yeni bir temsilci türü bildirilmesi gerekir.  
  
-   Bir temsilci örnekleme.  
  
     Bir temsilci türü bildirildikten sonra bir temsilci nesnesi oluşturulabilir ve belirli bir yöntem ile ilişkilendirilmiş. Önceki örnekte geçirerek bunu `PrintTitle` yönteme `ProcessPaperbackBooks` yöntem aşağıdaki örnekteki gibi:  
  
     [!code-csharp[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     Bu ile ilişkili yeni bir temsilci nesnesi oluşturur [statik](../../../csharp/language-reference/keywords/static.md) yöntemi `Test.PrintTitle`. Benzer şekilde, statik olmayan yöntemi `AddBookToTotal` nesne üzerinde `totaller` aşağıdaki örnekteki geçirilir:  
  
     [!code-csharp[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     Yeni bir temsilci nesnesi geçirilir her iki durumda da `ProcessPaperbackBooks` yöntemi.  
  
     Bir temsilci oluşturulduktan sonra, hiçbir zaman değişikliklerle ilişkili yöntemdir; temsilci nesneleri değişmez.  
  
-   Bir temsilci çağrılıyor.  
  
     Temsilci nesne oluşturulduktan sonra temsilci nesnesini genellikle temsilci çağıracak diğer kod geçirilir. Temsilci nesnesini, temsilciye geçirilecek parantez içine alınmış bağımsız değişkenler ve ardından temsilci nesnesinin adı kullanılarak çağrılır. Aşağıda, bir temsilci çağrı örneğidir:  
  
     [!code-csharp[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     Bir temsilci ya da zaman uyumlu olarak, bu örnekte olduğu gibi veya zaman uyumsuz olarak kullanarak çağrılabilir `BeginInvoke` ve `EndInvoke` yöntemleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Olaylar](../../../csharp/programming-guide/events/index.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
