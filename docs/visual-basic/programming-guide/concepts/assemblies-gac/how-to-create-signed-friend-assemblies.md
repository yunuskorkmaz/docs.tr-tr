---
title: "Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f87f816992bdfa9ed347c35ba651c59187551772
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="08865-102">Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="08865-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="08865-103">Bu örnek güçlü adlara sahip Derlemelerle arkadaş derlemeleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="08865-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="08865-104">Her iki derlemeleri strong adlandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="08865-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="08865-105">Bu örnekte her iki derlemeleri aynı anahtarlar kullansa da, anahtarları farklı iki derlemeler için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08865-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="08865-106">İmzalı bir derleme ve bir derlemeyi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="08865-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="08865-107">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="08865-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="08865-108">Aşağıdaki komut dizisi tanımlayıcı ad aracı ile bir keyfile oluşturmak ve ortak anahtar görüntülemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="08865-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="08865-109">Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="08865-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="08865-110">Bu örnek için bir tanımlayıcı ad anahtar oluştur ve FriendAssemblies.snk dosyada saklayabilir:</span><span class="sxs-lookup"><span data-stu-id="08865-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="08865-111">Ortak anahtar FriendAssemblies.snk ayıklayın ve FriendAssemblies.publickey koyun:</span><span class="sxs-lookup"><span data-stu-id="08865-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="08865-112">FriendAssemblies.publickey dosyasında depolanan genel anahtarını görüntüleyin:</span><span class="sxs-lookup"><span data-stu-id="08865-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="08865-113">Adlı bir Visual Basic dosyası oluşturma `friend_signed_A` aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="08865-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="08865-114">Kod kullanan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> friend_signed_B Arkadaş derlemesi olarak bildirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="08865-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="08865-115">Tanımlayıcı ad aracı her çalıştığında yeni bir ortak anahtar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="08865-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="08865-116">Bu nedenle, aşağıdaki örnekte gösterildiği gibi az önce oluşturulan, ortak anahtar ile aşağıdaki kodu ortak anahtar değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="08865-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  <span data-ttu-id="08865-117">Derleme ve friend_signed_A aşağıdaki komutu kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="08865-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="08865-118">Adlı bir Visual Basic dosyası oluşturma `friend_signed_B` ve aşağıdaki kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="08865-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="08865-119">Friend_signed_A friend_signed_B arkadaş derleme olarak belirttiğinden friend_signed_B kodda erişebilirsiniz `Friend` türleri ve friend_signed_A üyelerinden.</span><span class="sxs-lookup"><span data-stu-id="08865-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="08865-120">Dosya şu kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="08865-120">The file contains the following code.</span></span>  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  <span data-ttu-id="08865-121">Derleme ve friend_signed_B aşağıdaki komutu kullanarak oturum açın.</span><span class="sxs-lookup"><span data-stu-id="08865-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="08865-122">Derleyici tarafından üretilen derlemenin adını geçirilen arkadaş derleme adı eşleşmelidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="08865-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="08865-123">Kullanarak açıkça derleme ayarlayabilirsiniz `/out` derleyici seçeneği.</span><span class="sxs-lookup"><span data-stu-id="08865-123">You can explicitly set the assembly by using the `/out` compiler option.</span></span> <span data-ttu-id="08865-124">Daha fazla bilgi için bkz: [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="08865-124">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="08865-125">Friend_signed_B.exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="08865-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="08865-126">Program "Class1.Test" dizesi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="08865-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="08865-127">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="08865-127">.NET Framework Security</span></span>  
 <span data-ttu-id="08865-128">Arasındaki benzerlikler vardır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği ve <xref:System.Security.Permissions.StrongNameIdentityPermission> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="08865-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="08865-129">Ana fark <xref:System.Security.Permissions.StrongNameIdentityPermission> kodu, belirli bir bölüme çalıştırmak için güvenlik izinleri ancak talep <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği denetler görünürlüğünü `Friend` türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="08865-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08865-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08865-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="08865-131">Derlemeler ve Genel Derleme Önbelleği (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08865-131">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="08865-132">Arkadaş derlemeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08865-132">Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="08865-133">Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="08865-133">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="08865-134">/ keyfile</span><span class="sxs-lookup"><span data-stu-id="08865-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="08865-135">Sn.exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="08865-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="08865-136">Oluşturma ve tanımlayıcı adlı derlemeler kullanma</span><span class="sxs-lookup"><span data-stu-id="08865-136">Creating and Using Strong-Named Assemblies</span></span>](https://msdn.microsoft.com/library/xwb8f617)  
 [<span data-ttu-id="08865-137">Programlama Kavramları</span><span class="sxs-lookup"><span data-stu-id="08865-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
