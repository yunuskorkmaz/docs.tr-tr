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
ms.openlocfilehash: bb5978859ba25e1595ac3da7a2d7dad8cc2cad85
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041108"
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a>Nasıl yapılır: bir derlemeyi belirlemek&#39;s tam adı
Genel Derleme Önbelleği Aracı genel bütünleştirilmiş kod önbelleğindeki bir derleme tam olarak nitelenmiş adını bulmak için kullanın ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md)). Bkz: [nasıl yapılır: genel derleme önbelleğinin içeriğini görüntülemek](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md).  
  
 Genel derleme önbelleğinde bulunmayan derlemeler için çeşitli yollarla tam derleme adını alabilirsiniz: kod, bilgileri konsola veya bir değişkene çıkarmak için kullanabilirsiniz veya kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)tam adını içeren derlemenin meta verilerini incelemek için.  
  
-   Derleme uygulama tarafından zaten yüklü değilse, değeri alabilir <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> tam olarak nitelenmiş adını almak için özellik. Derlemeyi GAC içinde olup olmadığını bu yaklaşımı kullanabilirsiniz. Örnek, bir gösterim sağlar.  
  
-   Derlemenin dosya sistemi yolu biliyorsanız, statik çağırabilir (`Shared` Visual Basic'te) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> tam derleme adını almak için yöntemi. Basit bir örnek verilmiştir.  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tam adını içeren derlemenin meta verilerini incelemek için.  
  
 Sürüm, kültür ve derleme adı gibi derleme özniteliklerinin ayarlanması hakkında daha fazla bilgi için bkz: [derleme özniteliklerini ayarlama](../../../docs/framework/app-domains/set-assembly-attributes.md). Bir derlemeyi güçlü bir isim verilmesi hakkında daha fazla bilgi için bkz. [bkz](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, belirtilen bir sınıfı içeren bir derlemenin tam olarak nitelendirilmiş adını konsolda nasıl görüntüleyeceğinizi gösterir. Uygulama zaten yüklü bir derlemenin adını alır çünkü derlemeyi GAC'ye olup bir önemi yoktur.  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
- [Bütünleştirilmiş Kod Adları](../../../docs/framework/app-domains/assembly-names.md)  
- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
- [Kesin Adlandırılmış Bütünleştirilmiş Kodlar Oluşturma ve Kullanma](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
