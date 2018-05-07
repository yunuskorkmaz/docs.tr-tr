---
title: Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acef752cf54d28dd1f07431b5dbbadbac0b7849e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="blittable-and-non-blittable-types"></a>Blok Halinde Kopyalanabilir ve Kopyalanamaz Türler
Çoğu veri türleri, yönetilen ve yönetilmeyen bellekte ortak bir gösterimi olan ve birlikte çalışma sıralayıcı tarafından özel işlem gerektirmez. Bu tür adlı *blittable türleri* arasında geçirildiğinde bunlar dönüştürme gerektirmediği için yönetilen ve yönetilmeyen kodu.  
  
 Platformundan döndürülen yapıları çağırma çağrıları blittable türleri olması gerekir. Platform çağırma blittable olmayan yapıları dönüş türleri olarak desteklemez.  
  
 Aşağıdaki türleri <xref:System> ad alanı blittable türleri şunlardır:  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 Aşağıdaki karmaşık türler de blittable türleri şunlardır:  
  
-   Blittable türleri dizisi gibi tek boyutlu dizi. Ancak, bir değişken dizisini blittable türleri içeren bir tür kendisini değil blok halinde kopyalanabilir.  
  
-   Yalnızca blittable türleri (ve biçimlendirilmiş türleri olarak sıralanmış varsa sınıfları) içeren biçimlendirilmiş değer türleri. Biçimlendirilmiş değer türleri hakkında daha fazla bilgi için bkz: [değer türleri için varsayılan hazırlama](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100)).  
  
 Nesne başvuruları blittable değil. Bu başvurular blittable tek başına nesneler dizisi içerir. Örneğin, blittable olan bir yapı tanımlayabilirsiniz, ancak bu yapıların başvurularını dizisini içeren bir blittable türü tanımlayamazsınız.  
  
 Blok halinde kopyalanabilir türler yalnızca blittable üyeleri içeren sınıflar ve dizi bir iyileştirme olan [sabitlenmiş](../../../docs/framework/interop/copying-and-pinning.md) sıralama sırasında yerine kopyalanır. Bu tür çağıran ve çağrılan aynı grupta olduğunda olarak In/Out parametreleri sıralanması görünebilir. Ancak, bu tür gerçekte olduğu gibi parametreleri sıralanmış ve uygulamalısınız <xref:System.Runtime.InteropServices.InAttribute> ve <xref:System.Runtime.InteropServices.OutAttribute> bağımsız değişkeni olarak bir giriş/çıkış parametresi hazırlamak istiyorsanız öznitelikleri.  
  
 Bazı yönetilen veri türleri farklı gösterimi yönetilmeyen bir ortamda gerektirir. Bu blittable olmayan veri türleri sıralanabilir bir forma dönüştürülmesi gerekir. Örneğin, yönetilen dizeler kopyalanamaz türler şunlardır: çünkü bunlar sıralanabilir önce dize nesnelerini dönüştürülmelidir.  
  
 Aşağıdaki tabloda blittable olmayan türlerinden listeler <xref:System> ad alanı. [Temsilciler](https://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2(v=vs.100)), bir statik yöntem ya da bir sınıf örneği veri yapılarını olduğu olan ayrıca kopyalanamaz.  
  
|Örnekteki türü|Açıklama|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.|  
|[System.Boolean](https://msdn.microsoft.com/library/d4c00537-70f7-4ca6-8197-bfc1ec037ff9(v=vs.100))|1, 2 veya 4-bayt değeri ile dönüştürür `true` 1 veya -1 olarak.|  
|[System.Char](https://msdn.microsoft.com/library/cecc87c1-075e-4cde-aa56-33d189f66feb(v=vs.100))|Unicode veya ANSI karakter türüne dönüştürür.|  
|[System.Class](https://msdn.microsoft.com/library/fe334af5-0123-43d8-be84-26f6f023ddb6(v=vs.100))|Bir sınıf arabirimi dönüştürür.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Bir değişken veya arabirim dönüştürür.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|BSTR veya null başvuru sonlandırma bir dizeye dönüştürür.|  
|[System.Valuetype](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100))|Bir sabit bellek düzeni yapısıyla dönüştürür.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Bir C tarzı diziye dönüştürür veya `SAFEARRAY`.|  
  
 Sınıf ve nesne türleri yalnızca COM birlikte çalışma tarafından desteklenir. Karşılık gelen türlerin [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# ve C++, bkz: [sınıf kitaplığına genel bakış](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varsayılan Hazırlama Davranışı](../../../docs/framework/interop/default-marshaling-behavior.md)
