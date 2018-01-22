---
title: "COM Bileşenlerini .NET Framework'te Gösterme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d7cbef9247b82268b8006d640b967ffd03ae6717
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="exposing-com-components-to-the-net-framework"></a>COM Bileşenlerini .NET Framework'te Gösterme
Bu bölümde, yönetilen kod için var olan bir COM bileşeni kullanıma sunmak için gereken işlem özetlenmektedir. COM sunucuları bu sıkı bir şekilde yazma hakkında ayrıntılar .NET Framework ile tümleştirmek için bkz: [birlikte çalışma için tasarım değerlendirmeleri](http://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689).  
  
 Var olan COM bileşenlerini değerli yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevselliği olarak kaynaklardır. İdeal bir bileşen birincil birlikte çalışma derlemesi vardır ve COM tarafından uygulanan programlama standartlara sıkıca uyumlu  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>COM bileşenlerini .NET Framework'te kullanıma sunmak için  
  
1.  [Tür kitaplığını derleme olarak içeri aktarma](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).  
  
     Ortak dil çalışma zamanı meta veri COM türleri dahil olmak üzere tüm türleri için gerektirir. Meta veri içeri COM türlerini içeren bir derlemenin almak için birkaç yolu vardır.  
  
2.  [Yönetilen kodda COM türlerini oluşturabilir](http://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
     COM türlerini inceleyin, örnekleri etkinleştirin ve COM nesnesinin yöntemlerde, herhangi bir yönetilen türü için aynı şekilde çağırır.  
  
3.  [Birlikte çalışma projesi derleme](../../../docs/framework/interop/compiling-an-interop-project.md).  
  
     [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Çeşitli diller uyumlu ile ortak dil belirtimi (de dahil olmak üzere CLS), derleyicileri sağlayan [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# ve C++.  
  
4.  [Birlikte çalışma uygulamasını dağıtma](../../../docs/framework/interop/deploying-an-interop-application.md).  
  
     Birlikte çalışma uygulamaları olarak en iyi dağıtıldığı [tanımlayıcı adlı](../../../docs/framework/app-domains/strong-named-assemblies.md), genel derleme önbelleğinde imzalanmış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilmeyen Kod ile Birlikte Çalışma](../../../docs/framework/interop/index.md)  
 [Birlikte çalışma için tasarım konuları](http://msdn.microsoft.com/library/b59637f6-fe35-40d6-ae72-901e7a707689)  
 [COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
