---
title: Dizileri Bağımsız Değişkenler Olarak Geçirme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: d863cdc33a8a1a844aabbea9ba5876614e6e8dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a>Dizileri Bağımsız Değişkenler Olarak Geçirme (C# Programlama Kılavuzu)
Dizileri bağımsız değişkenler olarak yöntemi parametrelerine geçirilebilir. Diziler başvuru türleri olduğundan, yöntemi öğelerinin değerini değiştirebilirsiniz.  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a>Tek boyutlu diziler bağımsız değişkenler olarak geçirme  
 Başlatılmış bir tek boyutlu dizi yönteme geçirebilirsiniz. Örneğin, aşağıdaki deyim yazdırma yöntemi için bir dizi gönderir.  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 Aşağıdaki kod bir kısmi yazdırma yöntemi gösterir.  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 Başlatma ve tek bir adımda aşağıdaki örnekte gösterildiği gibi yeni bir dizi geçirin.  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, bir dizeler dizisi başlatılır ve bağımsız değişken olarak geçirilen bir `PrintArray` dizeleri yöntemi. Yöntem dizinin öğelerini görüntüler. Ardından, yöntemleri `ChangeArray` ve `ChangeArrayElement` bir dizi bağımsız değişkeni değere göre gönderme değişiklikleri dizi öğelerine engellemez olduğunu göstermek için çağrılır.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a>Çok boyutlu diziler bağımsız değişkenler olarak geçirme  
 Tek boyutlu dizi geçirdiğiniz aynı şekilde başlatılmış boyutlu bir diziye bir yönteme geçirin.  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 Aşağıdaki kod, iki boyutlu bir dizi bağımsız değişkeni olarak kabul eden bir yazdırma yöntemini kısmi bildirimini gösterir.  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 Başlatma ve tek bir adımda aşağıdaki örnekte gösterildiği gibi yeni bir dizi geçirin.  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnekte, iki boyutlu dizisi başlatılır ve geçirilen `Print2DArray` yöntemi. Yöntem dizinin öğelerini görüntüler.  
  
### <a name="code"></a>Kod  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Tek Boyutlu Diziler](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Çok Boyutlu Diziler](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [Düzensiz Diziler](../../../csharp/programming-guide/arrays/jagged-arrays.md)
