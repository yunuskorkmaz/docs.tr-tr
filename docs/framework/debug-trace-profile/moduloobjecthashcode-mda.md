---
title: moduloObjectHashcode MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d8f6975d117d9920d2199c3996246822d1fdb6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170787"
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
`moduloObjectHashcode` Yönetilen hata ayıklama Yardımcısı (MDA) davranışını değiştirir <xref:System.Object> sınıf gerçekleştirmek için bir işlem tarafından döndürülen ilişkin karma kodu modül <xref:System.Object.GetHashCode%2A> yöntemi. Bu MDA için'varsayılan mod neden olan 1 ' dir <xref:System.Object.GetHashCode%2A> 0 tüm nesneleri için döndürülecek.  
  
## <a name="symptoms"></a>Belirtiler  
 Ortak dil çalışma zamanı (CLR) yeni bir sürüme taşıdıktan sonra bir program artık düzgün şekilde çalışır:  
  
-   Program, yanlış nesneden alınırken bir <xref:System.Collections.Hashtable>.  
  
-   Sabit listesinden alınmış sırasını bir <xref:System.Collections.Hashtable> programın sonu değişmedi.  
  
-   Artık eşit olacak şekilde kullanılan iki nesne eşit değildir.  
  
-   Eşit olmaması için kullanılan iki nesne eşit olur.  
  
## <a name="cause"></a>Sebep  
 Programınızı yanlış nesneden alma bir <xref:System.Collections.Hashtable> çünkü yürütmesinin <xref:System.Object.Equals%2A> anahtarını sınıfındaki yöntemi <xref:System.Collections.Hashtable> çağrı sonuçlarını karşılaştırarak nesnelerin eşitliği testleri <xref:System.Object.GetHashCode%2A> yöntemi . Karma kodları, kendi ilgili alanlarını farklı değerlere sahip olsa bile iki nesnenin aynı karma koda sahip olabileceği için nesne eşitliği test etmek için kullanılmamalıdır. Bu karma kod çakışmaları ender olsa, uygulamada oluşur. Bu sahip olduğu etkiyi bir <xref:System.Collections.Hashtable> arama, eşit olacak şekilde eşit olmayan iki anahtar görünür ve yanlış nesne öğesinden döndürülen <xref:System.Collections.Hashtable>. Performans nedenleriyle yürütmesinin <xref:System.Object.GetHashCode%2A> sonraki sürümlerinde bir sürümünde gerçekleşmeyebilir çakışmaları oluşabilir için çalışma zamanı sürümleri arasında geçiş. Bu mda'nın karma kodları birbiriyle çakışır olduğunda, kod hataları olup olmadığını test etmek etkinleştirin. Etkin olduğunda, bu mda'nın neden <xref:System.Object.GetHashCode%2A> 0, döndürülecek yöntemi çakışmadan tüm karma kodları kaynaklanan. Yalnızca etkin bu MDA, programınızın olmalıdır, programınızı daha yavaş çalıştırır etkinleştirmektir.  
  
 Sabit listesinden alınmış sırasını bir <xref:System.Collections.Hashtable> bir çalışma zamanı sürümünden anahtar değişikliği için karma kodları hesaplamak için kullanılan algoritma için başka bir IF değişebilir. Programınız bir bağımlılık anahtarlar veya değerler dışında bir karma tablo numaralandırmasını bazında sürdü olup olmadığını test etmek için bu mda'nın etkinleştirebilirsiniz.  
  
## <a name="resolution"></a>Çözüm  
 Nesne kimliği için bir alternatif olarak, hiçbir zaman karma kodları kullanın. Geçersiz kılmasını uygulamak <xref:System.Object.Equals%2A?displayProperty=nameWithType> karma kodları değil karşılaştırmak için yöntemi.  
  
 Anahtarlar veya değerler numaralandırmalar bazında bağımlılıkları karma tabloları oluşturmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu MDA etkinleştirildiğinde uygulamaları daha yavaş çalışır. Bu MDA, yalnızca döndürülen ilişkin karma kodu alır ve bunun yerine bir modül tarafından bölündüğünde kalanı döndürür.  
  
## <a name="output"></a>Çıkış  
 Bu MDA için'hiçbir çıktı yok.  
  
## <a name="configuration"></a>Yapılandırma  
 `modulus` İlişkin karma kod üzerinde kullanılan mod özniteliği belirtir. Varsayılan değer 1’dir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
