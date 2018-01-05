---
title: moduloObjectHashcode MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 618196473e8e947e84b0506771bce84ee71a1c2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="moduloobjecthashcode-mda"></a>moduloObjectHashcode MDA
`moduloObjectHashcode` Yönetilen hata ayıklama Yardımcısı (MDA) davranışını değiştirir <xref:System.Object> sınıfı gerçekleştirmek için bir işlem tarafından döndürülen karma kodu modulo <xref:System.Object.GetHashCode%2A> yöntemi. Bu MDA varsayılan mod neden olan 1 ' dir <xref:System.Object.GetHashCode%2A> tüm nesneleri için 0 dönün.  
  
## <a name="symptoms"></a>Belirtiler  
 Ortak dil çalışma zamanı (CLR) yeni bir sürüme taşıdıktan sonra bir program artık düzgün şekilde çalışır:  
  
-   Program yanlış nesneden alınırken bir <xref:System.Collections.Hashtable>.  
  
-   Numaralandırma içinden sırasını bir <xref:System.Collections.Hashtable> program keser bir değişiklik vardır.  
  
-   Eşit olması için kullanılan iki nesne artık eşit değildir.  
  
-   Eşit olmaması için kullanılan iki nesne eşit.  
  
## <a name="cause"></a>Sebep  
 Programınızı yanlış nesnesinden alma bir <xref:System.Collections.Hashtable> çünkü uygulanması <xref:System.Object.Equals%2A> anahtara sınıfında yöntemi <xref:System.Collections.Hashtable> çağrısı sonuçlarını karşılaştırarak nesnelerin eşitlik için test <xref:System.Object.GetHashCode%2A> yöntemi . Karma kodlarını kendi ilgili alanlarını farklı değerlere sahip olsa bile iki nesnenin aynı karma koda sahip olabileceği için nesnenin eşitlik için test etmek için kullanılmamalıdır. Bu karma kodu çakışmaları ender olsa, uygulamada oluşur. Bu açmıştır etkili bir <xref:System.Collections.Hashtable> arama, eşit olmayan iki anahtar görünüyor eşit ve yanlış nesne sunucudan döndürülen <xref:System.Collections.Hashtable>. Performans nedenleriyle uygulanması <xref:System.Object.GetHashCode%2A> bir sürümünde gerçekleşmeyebilir çakışmaları oluşabilir ve sonraki sürümlerinde şekilde çalışma zamanı sürümleri arasında değiştirebilirsiniz. Karma kodlarını birbiriyle çakışır zaman kodunuzu hataları olup olmadığını sınamak bu MDA etkinleştirin. Etkinleştirildiğinde, bu MDA neden olan <xref:System.Object.GetHashCode%2A> 0, döndürülecek yöntemi yazılımlarla çakışma tüm karma kodlarını sonuçlanır. Yalnızca etkin bu MDA programınızın olmalıdır programınız daha yavaş çalışır etkinleştirmektir.  
  
 Numaralandırma içinden sırasını bir <xref:System.Collections.Hashtable> bir çalışma zamanı sürümünden anahtar değişikliği için karma kodları hesaplamak için kullanılan algoritma için başka bir if değişebilir. Programınızı bir bağımlılık anahtarları ve değerleri bir karma tablosu dışında numaralandırması terabayt sürdü olup olmadığını sınamak için bu MDA etkinleştirebilirsiniz.  
  
## <a name="resolution"></a>Çözüm  
 Hiç karma kodlarını nesne kimliği için bir yedek olarak kullanın. Geçersiz kılma uygulamak <xref:System.Object.Equals%2A?displayProperty=nameWithType> karma kodlarını değil Karşılaştırılacak yöntemi.  
  
 Numaralandırmalar anahtarları ve değerleri terabayt bağımlılıkları karma tablolarda oluşturmayın.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA etkinleştirildiğinde, uygulamaları daha yavaş çalışır. Bu MDA yalnızca döndürülen karma kodu alır ve bunun yerine bir modül tarafından bölünmüş zaman kalanı döndürür.  
  
## <a name="output"></a>Çıkış  
 Bu MDA hiçbir çıktısı yok.  
  
## <a name="configuration"></a>Yapılandırma  
 `modulus` Özniteliği, karma kod kullanılan modül belirtir. Varsayılan değer 1’dir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
