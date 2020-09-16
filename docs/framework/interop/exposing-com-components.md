---
title: COM Bileşenlerini .NET Framework'te Gösterme
description: COM bileşenlerini .NET 'e gösterme sürecini öğrenin. COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerlidir.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
ms.openlocfilehash: 34dda58d9513874169927164706fafdd95e8ed84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554188"
---
# <a name="exposing-com-components-to-the-net-framework"></a>COM Bileşenlerini .NET Framework'te Gösterme
Bu bölümde, mevcut bir COM bileşenini yönetilen koda göstermek için gereken işlem özetlenmektedir. .NET Framework ile sıkı bir şekilde tümleştirilen COM sunucularının yazılmasına ilişkin ayrıntılar için bkz. [Interoperation Için tasarım konuları](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).
  
 Mevcut COM bileşenleri, yönetilen kodda orta katman iş uygulamaları veya yalıtılmış işlevler olarak değerli kaynaklardır. İdeal bir bileşen bir birincil birlikte çalışma derlemesine sahiptir ve COM tarafından uygulanan programlama standartlarına sıkı bir şekilde uyumlu değildir.  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a>COM bileşenlerini .NET Framework kullanıma sunmak için  
  
1. [Bir tür kitaplığını derleme olarak Içeri aktarın](importing-a-type-library-as-an-assembly.md).  
  
     Ortak dil çalışma zamanı, COM türleri dahil olmak üzere tüm türler için meta veriler gerektirir. Meta veri olarak içeri aktarılan COM türlerini içeren bir derlemeyi almanın birkaç yolu vardır.  
  
2. [Yönetilen KODDA com türlerini kullanın](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).  
  
     Com türlerini inceleyebilir, örnekleri etkinleştirebilir ve COM nesnesi üzerinde yöntemleri herhangi bir yönetilen tür için yaptığınız şekilde çağırabilirsiniz.  
  
3. [Birlikte çalışabilirlik projesi derleyin](compiling-an-interop-project.md).  
  
     Windows SDK, Visual Basic, C# ve C++ dahil olmak üzere ortak dil belirtimi (CLS) ile uyumlu birkaç dil için derleyiciler sağlar.  
  
4. [Birlikte çalışabilirlik uygulaması dağıtın](deploying-an-interop-application.md).  
  
     Birlikte çalışma uygulamaları, genel derleme önbelleğinde [tanımlayıcı adlı](../../standard/assembly/strong-named.md), imzalanmış derlemeler olarak en iyi şekilde dağıtılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilmeyen Kod ile Birlikte Çalışma](index.md)
- [Birlikte çalışabilirlik için tasarım konuları](/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))
- [COM Birlikte Çalışma Örneği: .NET İstemcisi ve COM Sunucusu](com-interop-sample-net-client-and-com-server.md)
- [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../standard/language-independence-and-language-independent-components.md)
- [Gacutil.exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)](../tools/gacutil-exe-gac-tool.md)
