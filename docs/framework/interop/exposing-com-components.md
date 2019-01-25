---
title: COM Bileşenlerini .NET Framework'te Gösterme
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff12472ae5c7b2abbf1af338c2a1aea2a72907d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677153"
---
# <a name="exposing-com-components-to-the-net-framework"></a>COM Bileşenlerini .NET Framework'te Gösterme
Bu bölüm, yönetilen kod için varolan bir COM bileşeni kullanıma sunmak için gereken işlem özetler. COM sunucuları, sıkı bir şekilde yazma hakkında ayrıntılar .NET Framework ile tümleştirmek için bkz: [birlikte çalışma için tasarım konuları](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100)).
  
 Mevcut COM değerli kaynakları yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevi olarak bileşenlerdir. İdeal bir bileşeni olan birincil birlikte çalışma derlemesi ve sıkı bir şekilde COM tarafından uygulanan programlama standartlarına uyar  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>COM bileşenlerini .NET Framework'te göstermek için  
  
1.  [Bir tür kitaplığını derleme olarak içeri](importing-a-type-library-as-an-assembly.md).  
  
     Ortak dil çalışma zamanı, COM türleri dahil olmak üzere tüm türleri için meta verileri gerektirir. COM türleri olarak meta veriler içe içeren bir derlemenin almak için birkaç yolu vardır.  
  
2.  [Yönetilen kodda COM türleri oluşturma](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100)).  
  
     COM türlerini inceleyin, örnekleri etkinleştirmek ve herhangi bir yönetilen türü için yaptığınız gibi COM nesnesinin yöntemlerini çağırır.  
  
3.  [Birlikte çalışma projesi derleme](compiling-an-interop-project.md).  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Birçok dilde uyumlu olan ortak dil belirtimi (dahil olmak üzere CLS), derleyiciler sağlar [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#ve C++.  
  
4.  [Birlikte çalışma uygulamasını dağıtma](deploying-an-interop-application.md).  
  
     Birlikte çalışma uygulamaları olarak dağıtılan en iyi [tanımlayıcı adlı](../app-domains/strong-named-assemblies.md), genel derleme önbelleğinde derlemeleri imzalanmış.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilmeyen Kod ile Birlikte Çalışma](index.md)
- [Birlikte çalışma için tasarım konuları](https://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689(v=vs.100))
- [COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu](com-interop-sample-net-client-and-com-server.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
