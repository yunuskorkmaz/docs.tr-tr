---
title: ".NET Framework'te Konsol Uygulamaları Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e0bc3f14a3d21776506f0a269a1a8c9f970cac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="building-console-applications-in-the-net-framework"></a><span data-ttu-id="e2e6d-102">.NET Framework'te Konsol Uygulamaları Derleme</span><span class="sxs-lookup"><span data-stu-id="e2e6d-102">Building Console Applications in the .NET Framework</span></span>
<span data-ttu-id="e2e6d-103">.NET Framework uygulamalarında kullanma <xref:System.Console?displayProperty=nameWithType> karakterlerinden okumak ve konsola karakterleri yazmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-103">Applications in the .NET Framework can use the <xref:System.Console?displayProperty=nameWithType> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="e2e6d-104">Konsolundan veri standart giriş akışından okuma, verileri konsola standart çıktı akışına yazılır ve hata verileri konsola standart hata çıktı akışına yazılır.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-104">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="e2e6d-105">Konsol ile uygulama başlar ve bu olarak sunulduğunda bu akışları otomatik olarak ilişkilendirilir <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, ve <xref:System.Console.Error%2A> özellikleri, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-105">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>  
  
 <span data-ttu-id="e2e6d-106">Değeri <xref:System.Console.In%2A?displayProperty=nameWithType> özelliği bir <xref:System.IO.TextReader?displayProperty=nameWithType> , ancak nesne değerlerini <xref:System.Console.Out%2A?displayProperty=nameWithType> ve <xref:System.Console.Error%2A?displayProperty=nameWithType> özellikleri <xref:System.IO.TextWriter?displayProperty=nameWithType> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-106">The value of the <xref:System.Console.In%2A?displayProperty=nameWithType> property is a <xref:System.IO.TextReader?displayProperty=nameWithType> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=nameWithType> and <xref:System.Console.Error%2A?displayProperty=nameWithType> properties are <xref:System.IO.TextWriter?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="e2e6d-107">Bu özellikleri akış girişi veya çıkışı için farklı bir konum işaret edecek şekilde edinerek konsol temsil etmeyen akışları ile ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-107">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="e2e6d-108">Bir dosyaya ayarlayarak çıkışı örneğin yönlendirebilirsiniz <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliğine bir <xref:System.IO.StreamWriter?displayProperty=nameWithType>, hangi yalıtan bir <xref:System.IO.FileStream?displayProperty=nameWithType> yoluyla <xref:System.Console.SetOut%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-108">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=nameWithType> property to a <xref:System.IO.StreamWriter?displayProperty=nameWithType>, which encapsulates a <xref:System.IO.FileStream?displayProperty=nameWithType> by means of the <xref:System.Console.SetOut%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e2e6d-109"><xref:System.Console.In%2A?displayProperty=nameWithType> Ve <xref:System.Console.Out%2A?displayProperty=nameWithType> özellikleri aynı akışa başvurmak gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-109">The <xref:System.Console.In%2A?displayProperty=nameWithType> and <xref:System.Console.Out%2A?displayProperty=nameWithType> properties do not need to refer to the same stream.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2e6d-110">Örnekler C#, Visual Basic ve C++ da dahil olmak üzere, konsol uygulamaları oluşturma hakkında daha fazla bilgi için belgelere bakın <xref:System.Console> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-110">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>  
  
 <span data-ttu-id="e2e6d-111">Konsol yoksa Windows tabanlı bir uygulama olduğu gibi bilgileri yazma konsola olduğundan standart çıkış akışına yazılan çıktı görünür olmaz.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-111">If the console does not exist, as in a Windows-based application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="e2e6d-112">Bilgi erişilemeyen bir konsola yazma oluşturulması için bir özel duruma neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-112">Writing information to an inaccessible console does not cause an exception to be raised.</span></span>  
  
 <span data-ttu-id="e2e6d-113">Alternatif olarak, okuma ve Visual Studio kullanılarak geliştirilen Windows tabanlı bir uygulama içinde yazma Konsolu etkinleştirmek için projenin açın **özellikleri** iletişim kutusu, tıklatın **uygulama** sekme ve ayarlayın **uygulama türü** için **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-113">Alternately, to enable the console for reading and writing within a Windows-based application that is developed using Visual Studio, open the project's **Properties** dialog box, click the **Application** tab, and set the **Application type** to **Console Application**.</span></span>  
  
 <span data-ttu-id="e2e6d-114">Konsol uygulamaları varsayılan olarak başlatılır bir ileti Pompalama yoksundur.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-114">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="e2e6d-115">Bu nedenle, Microsoft Win32 zamanlayıcılar konsol çağrılar başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-115">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>  
  
 <span data-ttu-id="e2e6d-116">**System.Console** sınıfı karakterleri tek tek veya tüm satırları konsoldan okuyabilir yöntemleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-116">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="e2e6d-117">Diğer yöntemleri veri ve biçim dizelerini dönüştürmek ve ardından biçimlendirilmiş dizeler konsola yazma.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-117">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="e2e6d-118">Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e2e6d-118">For more information on formatting strings, see [Formatting Types](../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2e6d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e6d-119">See Also</span></span>  
 <xref:System.Console?displayProperty=nameWithType>  
 [<span data-ttu-id="e2e6d-120">Biçimlendirme türleri</span><span class="sxs-lookup"><span data-stu-id="e2e6d-120">Formatting Types</span></span>](../../docs/standard/base-types/formatting-types.md)
