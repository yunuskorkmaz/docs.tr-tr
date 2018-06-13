---
title: 'Nasıl yapılır: bir derlemeyi belirlemek&#39;s tam adı'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 663e7456337a2d9c413b15236e7ba1de33fbfa9b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743192"
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a>Nasıl yapılır: bir derlemeyi belirlemek&#39;s tam adı
Bir derlemeyi genel derleme önbelleğinde tam adını bulmak için Genel Derleme Önbelleği aracı kullanın ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Bkz: [nasıl yapılır: genel derleme önbelleğinin içeriğini görüntüleme](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Genel derleme önbelleğinde olmayan derlemeler için çeşitli yollarla tam nitelikli derleme adı elde edebilirsiniz: kod konsol veya bir değişken için bilgileri çıkarmak için kullanabilir veya kullanabilirsiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)tam adı içeren derlemenin meta verilerini incelemek için.  
  
-   Derleme uygulama tarafından zaten yüklü değilse, değeri alabilirsiniz <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> tam adı alınacağı özellik. Derlemesi GAC içinde olup olmadığını, bu yaklaşım kullanabilirsiniz. Örnek, bir gösterim sağlar.  
  
-   Derlemenin dosya sistemi yolu biliyorsanız, statik çağırabilirsiniz (`Shared` Visual Basic'te) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> tam nitelikli derleme adı almak için yöntemi. Basit bir örnek verilmiştir.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tam adı içeren derlemenin meta verilerini incelemek için.  
  
 Sürüm, kültür ve derleme adı gibi ayarı derleme öznitelikleri hakkında daha fazla bilgi için bkz: [ayarı derleme özniteliklerinin](../../../docs/framework/app-domains/set-assembly-attributes.md). Bir derleme tanımlayıcı bir ad verip hakkında daha fazla bilgi için bkz: [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, belirtilen bir sınıfı içeren bir derlemenin tam olarak nitelendirilmiş adını konsolda nasıl görüntüleyeceğinizi gösterir. Uygulama zaten yüklü bir derlemenin adını alır çünkü derlemesi GAC içinde olup olmadığını önemli değildir.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kod Adları](../../../docs/framework/app-domains/assembly-names.md)  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
